---
title: "Failure to Install Nvidia Driver"
date: 2011-05-07
forum: Multimedia Software
---

### Post by wookbok on 2011-05-07
I'm having issues installing the nvidia-96 driver package on the new Lubuntu 11.04. I have a GeForce4ti 4200 card and have had that driver package install successfuly on numerous flavors of Ubuntu over the years.

apt-get spits out the following error:

```
The following packages have unmet dependencies:
 nvidia-96 : Depends: xorg-video-abi-8.0 but it is not installable
             Depends: xserver-xorg-core (>= 2:1.8.99.905-1ubuntu3) but it is not going to be installed
```Meanwhile, a check of the currently installed xserver-xorg-core through apt-cache shows:

```
Package: xserver-xorg-core
Priority: optional
Section: x11
Installed-Size: 3736
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: i386
Source: xorg-server
Version: 2:1.10.1-1ubuntu1
Provides: xorg-input-abi-12, xorg-video-abi-10
...etc
```Apprently the xserver-xorg-core that comes with 11.04 includes xorg-video-abi-10, but nvidia-96 demands abi-8.0 and I'm wondering if I'll have to force a downgrade of xserver-xorg-core or if I can/should somehow roll back just xorg-video-abi to 8.0 seperately.

The nouveau driver does work, but I would really like full 3d acceleration like I have had in the past.

Any help would be appreciated

---

### Post by cavalier911 on 2011-05-07
```
sudo aptitude
```
Try to install the driver with aptitude.
Hopefully it will present at least one possible solution.

---

### Post by wookbok on 2011-05-08
results of sudo aptitude install nvidia-96:

```

The following NEW packages will be installed:
  acpid{a} dkms{a} nvidia-96{b} 
0 packages upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 8,782 kB of archives. After unpacking 26.3 MB will be used.
The following packages have unmet dependencies:
  nvidia-96: Depends: xorg-video-abi-8.0 which is a virtual package.
  xserver-xorg-core: Breaks: xserver-xorg-video-8 which is a virtual package.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     nvidia-96 [Not Installed]                          

Accept this solution? [Y/n/q/?] n

*** No more solutions available ***

```

---

