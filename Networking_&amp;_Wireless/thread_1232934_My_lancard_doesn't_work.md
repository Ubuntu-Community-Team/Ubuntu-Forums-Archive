---
title: "My lancard doesn't work"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by eleb on 2009-08-06
[http://ubuntuforums.org/showthread.php?t=1232213](http://ubuntuforums.org/showthread.php?t=1232213)
 
It's my last thread, Still disconnected from internet.
 
My lancard is wired, i try everything i could do.
 
 
 
```
sudo make install
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/gslinux/e100-3.5.17/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/gslinux/e100-3.5.17/src/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/gslinux/e100-3.5.17/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2

```
 
I did try to install drivers, but failed with that messages.:confused:
 
I need your help!
 
T^T

---

### Post by lisati on 2009-08-06
> **eleb said:**
> [http://ubuntuforums.org/showthread.php?t=1232213](http://ubuntuforums.org/showthread.php?t=1232213)
 
It's my last thread, Still disconnected from internet.
 
My lancard is wired, i try everything i could do.
 
 
 
```
sudo make install
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/gslinux/e100-3.5.17/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/gslinux/e100-3.5.17/src/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/gslinux/e100-3.5.17/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2

```
 
I did try to install drivers, but failed with that messages.:confused:
 
I need your help!
 
T^T
Any luck with the suggestions in your other thread?

---

### Post by eleb on 2009-08-06
Unfortunately, nope...

---

### Post by eleb on 2009-08-06
No ideas???
 
..
 
hopeless..

---

