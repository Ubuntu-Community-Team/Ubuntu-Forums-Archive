---
title: "Error when building AMD Catalyst 13.1 driver"
date: 2013-01-20
forum: Multimedia Software
---

### Post by bishop9226 on 2013-01-20
I am using 12.10 on a laptop with an hd7970m.  I am on 64 bit.  

sudo sh ./amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run --buildpkg Ubuntu/quantal

me@ubuntu:~/Desktop/amd$ sudo sh ./amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run --buildpkg Ubuntu/quantal^C
Created directory fglrx-install.OErhiS
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-9.012.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/quantal

Unable to install dpkg-dev.  Please manually install and try again.
Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
./packages/Ubuntu/ati-packager.sh: 295: ./packages/Ubuntu/ati-packager.sh: dpkg-buildpackage: not found
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
./packages/Ubuntu/ati-packager.sh: 295: ./packages/Ubuntu/ati-packager.sh: dpkg-buildpackage: not found
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
./packages/Ubuntu/ati-packager.sh: 295: ./packages/Ubuntu/ati-packager.sh: dpkg-buildpackage: not found
Removing temporary directory: fglrx-install.PGu5D4

---

### Post by edcv on 2013-01-22
Works fine for me. I guess your missing some packages.
Maybe dpkg?

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
3.1. worked fine for me

---

### Post by edcv on 2013-01-22
Btw. I had to reboot before fglrxinfo gave correct info

---

