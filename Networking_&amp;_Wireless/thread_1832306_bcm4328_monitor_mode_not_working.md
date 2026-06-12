---
title: "bcm4328 monitor mode not working"
date: 2011-08-24
forum: Networking &amp; Wireless
---

### Post by elleuh on 2011-08-24
hi, im having trouble getting my broadcom bcm4321 card into monitor mode.
i followed the tut in the sticky but when i type make this happens:

```
/ndiswrapper/ndiswrapper-1.56$ make
make -C driver
make[1]: Entering directory `/ndiswrapper/ndiswrapper-1.56/driver'
make -C /usr/src/linux-headers-2.6.38-11-generic M=/ndiswrapper/ndiswrapper-1.56/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  MKEXPORT /ndiswrapper/ndiswrapper-1.56/driver/ndis_exports.h
  CC [M]  /ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.o
  CC [M]  /ndiswrapper/ndiswrapper-1.56/driver/loader.o
/ndiswrapper/ndiswrapper-1.56/driver/loader.c:834:2: error: unknown field ‘ioctl’ specified in initializer
/ndiswrapper/ndiswrapper-1.56/driver/loader.c:834:2: warning: initialization from incompatible pointer type
make[3]: *** [/ndiswrapper/ndiswrapper-1.56/driver/loader.o] Error 1
make[2]: *** [_module_/ndiswrapper/ndiswrapper-1.56/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/ndiswrapper/ndiswrapper-1.56/driver'
make: *** [all] Error 2
henk@ubuntu:/ndiswrapper/ndiswrapper-1.56$ sudo apt-get remove ndiswrapper-common
[sudo] password for henk: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-common is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
henk@ubuntu:/ndiswrapper/ndiswrapper-1.56$ sudo checkinstall

checkinstall 1.6.2, Copyright 2009 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@ubuntu ]
1 -  Summary: [ Package created with checkinstall 1.6.2 ]
2 -  Name:    [ ndiswrapper ]
3 -  Version: [ 1.56 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ ndiswrapper-1.56 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ ndiswrapper ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make -C driver install
make[1]: Entering directory `/ndiswrapper/ndiswrapper-1.56/driver'
make -C /usr/src/linux-headers-2.6.38-11-generic M=/ndiswrapper/ndiswrapper-1.56/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  CC [M]  /ndiswrapper/ndiswrapper-1.56/driver/loader.o
/ndiswrapper/ndiswrapper-1.56/driver/loader.c:834:2: error: unknown field ‘ioctl’ specified in initializer
/ndiswrapper/ndiswrapper-1.56/driver/loader.c:834:2: warning: initialization from incompatible pointer type
make[3]: *** [/ndiswrapper/ndiswrapper-1.56/driver/loader.o] Error 1
make[2]: *** [_module_/ndiswrapper/ndiswrapper-1.56/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/ndiswrapper/ndiswrapper-1.56/driver'
make: *** [install] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```could somebody please help me to get it to work? 


some info if needed:
ubuntu 11.04
dell insprion 1720
broadcom wireless card 4328

---

### Post by SubSurge on 2012-08-17
Having the same exact problem! Help!

---

### Post by wildmanne39 on 2012-08-17
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

