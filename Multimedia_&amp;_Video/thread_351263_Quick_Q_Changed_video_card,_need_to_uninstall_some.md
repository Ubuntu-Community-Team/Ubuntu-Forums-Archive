---
title: "Quick Q: Changed video card, need to uninstall something to install new drivers"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by SimonTheMime on 2007-02-01
From ATI -> nVidia:

[php]dylan@room:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  nvidia-kernel-source
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4066kB of archives.
After unpacking 12.6MB of additional disk space will be used.
(Reading database ... 96787 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8776+2.6.17.7-10.1_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.8776+2.6.17.7-10.1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1.0.8776+2.6.17.7-10.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/php]

Edit: Fixed:
$ sudo dpkg-divert --package xorg-driver-fglrx --remove /usr/lib32/libGL.so.1
$ sudo dpkg-divert --package xorg-driver-fglrx --remove /usr/lib32/libGL.so.1.2
$ sudo apt-get install --reinstall xorg-driver-fglrx

---

### Post by lavid on 2007-02-01
How would one go about doing that to switch FROM the nvidia drivers to... say a mesagl implementation?

---

