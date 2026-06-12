---
title: "ATI Drivers once worked..."
date: 2008-09-13
forum: Multimedia Software
---

### Post by darkreaction on 2008-09-13
So When I first installed ubuntu I go the ati drivers running fine and now they Don't work I tried the tutorial on [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) but I always get > display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2) When I do > sudo apt-get remove xserver-xgl I come up with > Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xserver-xgl is not installed, so not removed
The following packages were automatically installed and are no longer required:
  gappletviewer-4.2 module-assistant x11proto-fonts-dev xserver-xorg-dev
  x11proto-video-dev libdns32 libxalan110
  virtualbox-ose-modules-2.6.24-16-generic apturl librsvg2-bin libpixman-1-dev
  dpatch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded. Can someone please give me a hand.

---

### Post by darkreaction on 2008-09-13
Sooooo no one?

---

### Post by darkreaction on 2008-09-14
OK so I found something that might be of interest. when I run.```
 sudo dpkg -i fglrx-kernel-source_8.522-0ubuntu1_i386.deb
``` I come up with this Error filled code.```
(Reading database ... 249551 files and directories currently installed.)
Preparing to replace fglrx-kernel-source 2:8.522-0ubuntu1 (using fglrx-kernel-source_8.522-0ubuntu1_i386.deb) ...
Removing all DKMS Modules
rpmdb: Program version 4.3 doesn't match environment version
error: db4 error(-30974) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 -  (-30974)
error: cannot open Packages database in /var/lib/rpm
rpmdb: Program version 4.3 doesn't match environment version
error: db4 error(-30974) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 -  (-30974)
error: cannot open Packages database in /var/lib/rpm
rpmdb: Program version 4.3 doesn't match environment version
error: db4 error(-30974) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 -  (-30974)
error: cannot open Packages database in /var/lib/rpm
Done.
Unpacking replacement fglrx-kernel-source ...
Setting up fglrx-kernel-source (2:8.522-0ubuntu1) ...
Adding Module to DKMS build system
rpmdb: Program version 4.3 doesn't match environment version
error: db4 error(-30974) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 -  (-30974)
error: cannot open Packages database in /var/lib/rpm
rpmdb: Program version 4.3 doesn't match environment version
error: db4 error(-30974) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 -  (-30974)
error: cannot open Packages database in /var/lib/rpm
rpmdb: Program version 4.3 doesn't match environment version
error: db4 error(-30974) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 -  (-30974)
error: cannot open Packages database in /var/lib/rpm
Doing initial module build
rpmdb: Program version 4.3 doesn't match environment version
error: db4 error(-30974) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 -  (-30974)
error: cannot open Packages database in /var/lib/rpm
rpmdb: Program version 4.3 doesn't match environment version
error: db4 error(-30974) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 -  (-30974)
error: cannot open Packages database in /var/lib/rpm
rpmdb: Program version 4.3 doesn't match environment version
error: db4 error(-30974) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 -  (-30974)
error: cannot open Packages database in /var/lib/rpm

Error!  Build of fglrx.ko failed for: 2.6.24-19-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.522/build/ for more information.
Installing initial module
rpmdb: Program version 4.3 doesn't match environment version
error: db4 error(-30974) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 -  (-30974)
error: cannot open Packages database in /var/lib/rpm
rpmdb: Program version 4.3 doesn't match environment version
error: db4 error(-30974) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 -  (-30974)
error: cannot open Packages database in /var/lib/rpm
rpmdb: Program version 4.3 doesn't match environment version
error: db4 error(-30974) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 -  (-30974)
error: cannot open Packages database in /var/lib/rpm

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.24-19-generic (i686) first.
Done.
```So can anyone Help?

---

