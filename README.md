# meta-kernel-dev
Upstream/LTS Kernel develop and Emulate Layer for OpenEmbedded/Yocto 

[![license](https://img.shields.io/github/license/mashape/apistatus.svg)](https://github.com/pino-kim/meta-kernel-dev/blob/master/LICENSE)


## Description

Status : on the working

This is the general Miscellaneous layer for the Kernel develpoer.


Part of meta-kernel-dev should work with different
OpenEmbedded/Yocto distributions and layer stacks, such as:

* Distro-less (only with OE-Core).
* Yocto/Poky (main focus of testing).

## Dependencies

This distro dependends on : 

* URI: git://github.com/openembedded/openembedded-core
  * branch: master
  * revision: HEAD
* URI: git://github.com/openembedded/bitbake
  * branch: master
  * revision: HEAD

## Quick Start

Note: You only need this if you do not have an existing Yocto Project build environment.

```text
 sudo apt-get install gawk wget git-core diffstat unzip texinfo gcc-multilib \
     build-essential chrpath socat cpio python python3 python3-pip python3-pexpect \
     xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev \
     xterm
```

You can find more information below site to set Yocto Project build environment.

Yocto Project Quick Build : [Build Host Packages](https://www.yoctoproject.org/docs/latest/brief-yoctoprojectqs/brief-yoctoprojectqs.html#brief-build-system-packages)

Make sure to [install the `repo` command by Google](https://source.android.com/setup/downloading#installing-repo) first. 

## Create workspace
```text
mkdir kernel-dev-yocto && cd kernel-dev-yocto
repo init -u git://github.com/pino-kim/meta-kernel-dev  -b master -m tools/manifests/kernel-dev.xml
repo sync
repo start work --all
```

## Update existing workspace

In order to bring all layers uptodate with upstream

```text
cd kernel-dev-yocto
repo sync
repo rebase
```
## Setup Build Environment
```text
. ./meta-kernel-dev/setup.sh
```

## Build Image

A console-only minimal size image
```text
bitbake core-image-minimal
```

## Run in QEMU
```text
runqemu nographic
```
