---
title: "Goggles / Ogle DVD player installation"
date: 2008-06-08
forum: Multimedia Software
---

### Post by ugm6hr on 2008-06-08
Has anyone successfully installed Goggles 0.9.1 ([http://www.fifthplanet.net/goggles.html](http://www.fifthplanet.net/goggles.html)) on Ubuntu 8.04 / Hardy?

There is no .deb for 0.9.1, and the 0.8 .deb is for i386 only.  Hence I am trying to install from source (ideally using checkinstall if possible) on 64-bit Ubuntu 8.04.

Dependencies:
Fox Toolkit 1.6 installed from aptitude (libfox-1.6-0)
libpng already present
Ogle 0.9.2 installed from aptitude (ogle)

However, the installation script can't find FOX:
```
 ./gb --fox-prefix=/usr/lib --ogle-prefix=/usr/bin
 - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
              Package: goggles
              Version: 0.9.1
 - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
              OS Name: Linux
           OS Release: 2.6.24-16-generic
           OS Machine: x86_64
 
         Build Config: build/config.linux_x86_64
 - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
 Check Byte Order    : Failed (using Little Endian instead)
 Check FOX Config    : Not Found
 Check FOX Library   : Not Found

```
It doesn't matter whether I use the prefix locations or not - ogle is definitely in /usr/bin, and libfox is in /usr/lib.

Where am I going wrong?

As for why?  I have found that none of the other media players supports DVD menus quite as well as ogle, and ogle-gui is not as good afront-end GUI as goggles (and also messes up full screen viewing).

---

