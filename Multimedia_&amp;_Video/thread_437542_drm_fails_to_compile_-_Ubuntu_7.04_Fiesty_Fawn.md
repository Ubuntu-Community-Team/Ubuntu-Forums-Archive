---
title: "drm fails to compile - Ubuntu 7.04 Fiesty Fawn"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by iclinux on 2007-05-08
hi,all, when compiling drm, I get the follow error, any suggetions? thanks

```
iclinux@iclinux:~/Desktop/drm/linux-core$ make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via
make -C /lib/modules/2.6.20-15-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/iclinux/Desktop/drm/linux-core/drm_stub.o
/home/iclinux/Desktop/drm/linux-core/drm_stub.c:51: [COLOR="Red"]error: size of array ‘type name’ is negative[/COLOR]
make[2]: *** [/home/iclinux/Desktop/drm/linux-core/drm_stub.o] Error 1
make[1]: *** [_module_/home/iclinux/Desktop/drm/linux-core] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2
iclinux@iclinux:~/Desktop/drm/linux-core$
```

---

### Post by oasick on 2007-05-15
I have this same problem to compile the mach64 driver for my compaq evo n400c

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/34590](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/34590) Here i'm looking for a solution

---

### Post by Offoffoff on 2007-07-03
I have just commented all suspicious lines - And got luck!

---

