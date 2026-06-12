---
title: "rt73-k2wrlz-3.0.3 with Ubuntu 10.04 not working"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by pebiman on 2010-06-01
Hello:

I'm having troubles building the rt73 injection driver in ubuntu 10.04.

This is what I got:

make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
rt73.ko failed to build!
make: *** [module] Error 1


Any ideas?.


Thanks

---

### Post by kutya61 on 2010-06-02
Hi,
I had this problem for months, and finally today found a soloution.
It is on this page: [http://forum.aircrack-ng.org/index.php?topic=1824.255]("http://forum.aircrack-ng.org/index.php?topic=1824.255")

You have to modify the Makefile from this:
```

ifdef TOPDIR
obj-m += $(MODULE_NAME).o
endif

```
to this:
```

#ifdef TOPDIR
obj-m += $(MODULE_NAME).o
#endif

```

and you have to change the rtmp_main.c file to the attached one in [this post]("http://forum.aircrack-ng.org/index.php?topic=1824.msg33360#msg33360").

I'm on karmic, but I hope, that this works in lucid also.

edit: and here is deb package for karmic, but didn't try it.
[https://edge.launchpad.net/~marco/+archive/ppa/+packages]("https://edge.launchpad.net/~marco/+archive/ppa/+packages")

---

