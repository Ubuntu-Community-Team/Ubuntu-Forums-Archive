---
title: "Problems installing ATI driver"
date: 2011-08-18
forum: Multimedia Software
---

### Post by Grotesque on 2011-08-18
I am using the new 11.04 version of ubuntu and following this guide to setup my video driver: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I get this error at step 11 after typing this command into terminal:
sudo sh ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/natty

==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/natty
Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions
Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions
Removing temporary directory: fglrx-install.AXpqfB

Any help appreciated.

---

### Post by pme 72 on 2011-08-20
First, check your graphic card name and chipset:

lspci -nn | grep VGA

---

