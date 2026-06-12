---
title: "Module fglrx does not exist in /proc/modules"
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by athanasios on 2007-12-09
ERROR: Module fglrx does not exist in /proc/modules

I tried to install ATI drivers with Envy 0.9.9 but without success.
This is the envy-install-log 

python pulse.py ati latest 

root@linux-sec:/usr/share/envy# python pulse.py ati latest

Envy - Version 0.9.9

Ubuntu Gutsy 32bit

OK: All the packages are installed

An installer has been detected

md5new: d784fa8b6d98d27699781bd9a7cf19f0

md5sumold: 099eead18eb845f83da1d743dc17cc47

ENVY ERROR: md5 Error! Trying to fetch the driver from the website

No installer detected

Download of the driver in progress, please wait

--11:27:25--  [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-7-11-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-7-11-x86.x86_64.run)

           => `ati-driver-installer-7-11-x86.x86_64.run'

Resolving a248.e.akamai.net... 81.23.243.135, 81.23.243.153

Connecting to a248.e.akamai.net|81.23.243.135|:443... connected.

WARNING: Certificate verification error for a248.e.akamai.net: unable to get local issuer certificate

HTTP request sent, awaiting response... 200 OK

Length: 47,667,647 (45M) [application/octet-stream]

100%[===========================================================================>] 47,667,647   207.96K/s    ETA 00:00



11:31:18 (200.72 KB/s) - `ati-driver-installer-7-11-x86.x86_64.run' saved [47667647/47667647]

md5new: 099eead18eb845f83da1d743dc17cc47

md5sumold: 099eead18eb845f83da1d743dc17cc47

Created directory fglrx-install.P19217

Verifying archive integrity... All good.

Uncompressing ATI Proprietary Linux Driver-8.433.......................................................................

.......................................................................................................................

.......................................................................................................................

.......................................................................................................................

.......................................................................................................................

...................................................................................................

==================================================

 ATI Technologies Linux Driver Installer/Packager 

==================================================

Generating package: Ubuntu/gutsy

Package /usr/share/envy/xorg-driver-fglrx_8.433-1_i386.deb has been successfully generated

Package /usr/share/envy/xorg-driver-fglrx-dev_8.433-1_i386.deb has been successfully generated

Package /usr/share/envy/fglrx-kernel-source_8.433-1_i386.deb has been successfully generated

Package /usr/share/envy/fglrx-amdcccle_8.433-1_i386.deb has been successfully generated

Removing temporary directory: fglrx-install.P19217

Selecting previously deselected package fglrx-amdcccle.

(Reading database ... 91995 files and directories currently installed.)

Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.433-1_i386.deb) ...

Selecting previously deselected package fglrx-kernel-source.

Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.433-1_i386.deb) ...

Selecting previously deselected package xorg-driver-fglrx-dev.

Unpacking xorg-driver-fglrx-dev (from xorg-driver-fglrx-dev_8.433-1_i386.deb) ...

Selecting previously deselected package xorg-driver-fglrx.

Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.433-1_i386.deb) ...

Setting up fglrx-kernel-source (8.433-1) ...

Setting up xorg-driver-fglrx (8.433-1) ...

Starting atieventsd: done.



Setting up fglrx-amdcccle (8.433-1) ...

Setting up xorg-driver-fglrx-dev (8.433-1) ...

Processing triggers for libc6 ...

ldconfig deferred processing now taking place

Getting source for kernel version: 2.6.22-14-generic

Kernel headers available in /usr/src/linux-headers-2.6.22-14-generic

Creating symlink...

apt-get install build-essential

Reading package lists... Done

Building dependency tree       

Reading state information... Done

build-essential is already the newest version.

build-essential set to manual installed.

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



Done!

Updated infos about 86 packages

Extracting the package tarball, /usr/src/fglrx.tar.bz2, please wait...

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Building fglrx-kernel-source, step 1, please wait... &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;                      

                      &#9474; Build starting...                                                       &#9474;                      

                      &#9474;                                                                         &#9474;                      

                      &#9474;                                                                         &#9474;                      

                      &#9474;                                                                         &#9474;                      

                      &#9474;                                                                         &#9474;                      

                      &#9474;                                                                         &#9474;                      

                      &#9474;                                                                         &#9474;                      

                      &#9474;                                                                         &#9474;                      

                      &#9474;                                                                         &#9474;                      

                      &#9474;                                                                         &#9474;                      

                      &#9474;                                                                         &#9474;



Selecting previously deselected package fglrx-kernel-2.6.22-14-generic.

(Reading database ... 92152 files and directories currently installed.)

Unpacking fglrx-kernel-2.6.22-14-generic (from .../fglrx-kernel-2.6.22-14-generic_8.433-1+2.6.22-14.46_i386.deb) ...

Setting up fglrx-kernel-2.6.22-14-generic (8.433-1+2.6.22-14.46) ...



ERROR: Module fglrx does not exist in /proc/modules

ENVY: Compiz is installed

ENVY: making Compiz configuration backup

ENVY: Operation Complete

If I boot normally I've a blank screen, so I can only enter under fail-safe gnome session.
I tried also with 'sudo depmod -ae' but the same problem continue.
Any idea please?

---

