---
title: "Orinoco gold card and monitor mode"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by jakev383 on 2008-12-22
I'm trying to get an Orinoco Gold card's monitor mode enabled for kismet.
I've tried the methods here:
[https://wiki.ubuntu.com/OrinocoMonitorMode](https://wiki.ubuntu.com/OrinocoMonitorMode)
But get this error for the v15 driver:
```

make -C /usr/src/linux-headers-2.6.27-7-generic M=/orinoco/orinoco-0.15 KERNELRELEASE=2.6.27-7-generic modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
/orinoco/orinoco-0.15/Kbuild:34: *** Wireless extensions are not enabled.  Stop.
make[1]: *** [_module_/orinoco/orinoco-0.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2
root@drive:/orinoco/orinoco-0.15# cd ..
root@drive:/orinoco# ifconfig ath0 up
root@drive:/orinoco# cd orinoco-0.15/
root@drive:/orinoco/orinoco-0.15# make
make -C /usr/src/linux-headers-2.6.27-7-generic M=/orinoco/orinoco-0.15 KERNELRELEASE=2.6.27-7-generic modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
/orinoco/orinoco-0.15/Kbuild:34: *** Wireless extensions are not enabled.  Stop.
make[1]: *** [_module_/orinoco/orinoco-0.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2

```
So I tried the v13e drivers also on the wiki, and get this error:
```

make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/orinoco/orinoco-0.13e-SN-8 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /orinoco/orinoco-0.13e-SN-8/hermes.o
/orinoco/orinoco-0.13e-SN-8/hermes.c:41:26: error: linux/config.h: No such file or directory
make[2]: *** [/orinoco/orinoco-0.13e-SN-8/hermes.o] Error 1
make[1]: *** [_module_/orinoco/orinoco-0.13e-SN-8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2

```

I also tried the instructions on this post:
[http://ubuntuforums.org/showthread.php?t=836102&highlight=orinoco](http://ubuntuforums.org/showthread.php?t=836102&highlight=orinoco)
And I get this error:
```

make -C /usr/src/linux-headers-2.6.27-7-generic M=/orinoco/orinoco-0.15 KERNELRELEASE=2.6.27-7-generic modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /orinoco/orinoco-0.15/orinoco_nortel.o
In file included from /orinoco/orinoco-0.15/orinoco_nortel.c:51:
/orinoco/orinoco-0.15/orinoco_pci.h: In function ‘orinoco_pci_resume’:
/orinoco/orinoco-0.15/orinoco_pci.h:67: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/orinoco/orinoco-0.15/orinoco_nortel.c: In function ‘orinoco_nortel_init_one’:
/orinoco/orinoco-0.15/orinoco_nortel.c:196: error: implicit declaration of function ‘SET_MODULE_OWNER’
/orinoco/orinoco-0.15/orinoco_nortel.c:202: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/orinoco/orinoco-0.15/orinoco_nortel.o] Error 1
make[1]: *** [_module_/orinoco/orinoco-0.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2

```

I've tired these with Ubuntu 8.04 and 8.10.  Is there a working method of getting the monitor mode to work with the Orinoco card?
Any help is appreciated!
Thanks.

---

