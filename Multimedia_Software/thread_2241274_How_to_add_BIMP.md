---
title: "How to add BIMP"
date: 2014-08-25
forum: Multimedia Software
---

### Post by satimis on 2014-08-25
Hi all,

Ubuntu 12.04 desktop 64bit

Please advise how to add BIMP, plugin to GIMP

BIMP. Batch Image Manipulation Plugin
[http://registry.gimp.org/node/26259](http://registry.gimp.org/node/26259)

Is it available on repo?  Or I have to download it on their website?

Thanks
satimis

---

### Post by slickymaster on 2014-08-25
Download it from [http://www.alessandrofrancesconi.it/projects/bimp/](http://www.alessandrofrancesconi.it/projects/bimp/)

You must install **libgimp2.0-dev** and **libpcre3-dev** packages in order to have the full set of libraries and dependences to compile BIMP. Then:```
make && make install
```or:```
make && sudo make install-admin
```to make and install for every user in the system (needs root privileges).

Make sure that the "bimp-locale" folder is copied in the plug-in directory too! If not, you can do it manually by copying it from ./bin/win32.
Don't mind the warnings...

---

