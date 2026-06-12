---
title: "visual effect are not working !"
date: 2010-08-22
forum: Multimedia Software
---

### Post by auzuliux on 2010-08-22
one weeks ago i buy a new laptop dell inspiron n4010 and installed ubuntu 10.04 LTS. now my visual effects are not working.
i have already installed comfiz comfig but it is not working .
here are some commands and their out put.
 

**lspci -nn | grep VGA**
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 12)


**sudo apt-get install compiz compizconfig-settings-manager**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
compizconfig-settings-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


**compiz --replace**
disabling 3D rasterization
flushing batchbuffer before/after each draw call
flushing GPU caches before/after each draw call
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

---

