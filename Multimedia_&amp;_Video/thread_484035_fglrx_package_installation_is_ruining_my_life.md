---
title: "fglrx package installation is ruining my life"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by bohsocks on 2007-06-25
Hi... when I try to install xorg-driver-fglrx, this happens:

rob@RLAPLINUX:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  xorg-driver-fglrx
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/6143kB of archives.
After unpacking 17.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 113514 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_7.1.0-8.34.8+2.6.20.5-16.28_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_7.1.0-8.34.8+2.6.20.5-16.28_i386.deb (--unpack):
 trying to overwrite `/usr/sbin/atigetsysteminfo.sh', which is also in package fglrx-4-3-0
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_7.1.0-8.34.8+2.6.20.5-16.28_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
rob@RLAPLINUX:~$ 

This problem is causing me to not be able to use Synaptic or to be able to use Update Manager.....

Any reason why this would be happening?

Sincerely,

Linux N00b

---

