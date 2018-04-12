# FSS2Linux

![N|FssLinux](http://www.fujitsu.com/global/resources/design/stylesheets/images/css_images/fujitsu/symbolmark.gif)

FSS2 Linux is based of poky 1.6, 3.x kernel and hosted on public github server maintained by Fujitsu organization. 
Following describes workflow and steps to download FSS2Linux from public github and create a working build environment.

## Installation

### Preprequites
#### Build system
FSS2Linux requires one of the following sanity tested distros for building distro.
    - Ubuntu-12.04
    - Ubuntu-13.10
    - Ubuntu-14.04
    - Fedora-19
    - Fedora-20
    - CentOS-6.4
    - CentOS-6.5
    - Debian-7.0
    - Debian-7.1
    - Debian-7.2
    - Debian-7.3
    - Debian-7.4
    - SUSE-LINUX-12.2
    - openSUSE-project-12.3
    - openSUSE-project-13.1

### Working with yocto build
Install the dependencies and devDependencies and restart the server.

```sh
$ sudo apt-get install git-core gnupg flex bison gperf zip curl zlib1g-dev gcc-multilib g++-multilib libc6-dev-i386 lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z-dev ccache libgl1-mesa-dev libxml2-utils xsltproc unzip
$ sudo apt-get install gawk wget git-core diffstat unzip texinfo gcc-multilib build-essential chrpath libsdl1.2-dev
```

### Install repo tools
repo tools is based off andriod project and required to build yocto

```sh
mkdir ~/bin
export PATH=~/bin:$PATH
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
cd ~/bin
chmod +x repo
```

### Configure Git for the first time
```sh
cd
git config --global user.name "your Name"
git config --global user.email "you@email.com"
```

## Building FSS2Linux

#### Qemux86-64 target
```sh
cd
mkdir working_dir
cd working_dir
repo init -u https://github.com/FujitsuNetworkCommunications/fss2-manifest
repo sync
source poky/fss2-init-build-dev
bitbake core-image-minimal
```

#### T600 PPC target
```sh
cd
mkdir working_dir
cd working_dir
repo init -u https://github.com/FujitsuNetworkCommunications/fss2-manifest
repo sync
source poky/fss2-init-build-dev -m t600
bitbake core-image-minimal
```


License
----

GPLv2         [GPLv2](https://foobar.org)
Fujitsu       [Fujitsu GPL](https://foobar.org)
