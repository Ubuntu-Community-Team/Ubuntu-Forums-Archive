---
title: "ubuntu alsa not compiling for audioscience"
date: 2006-11-06
forum: Multimedia &amp; Video
---

### Post by prune on 2006-11-06
Hi,

I'm trying to have an AudioScience pci card (model 6416) working on ubuntu 6.10.
The kernel module, part of alsa since 1.0.7, is not present in ubuntu where alsa 1.0.11 is bundled (can you tell me why ? ).

I first thought at getting alsa-source using atp-get and compile the missing module. This is what I get :

make -C /lib/modules/2.6.17-10-server/build SUBDIRS=/usr/src/modules/alsa-driver  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-server'
  CC [M]  /usr/src/modules/alsa-driver/pci/asihpi/hpimod.o
/usr/src/modules/alsa-driver/pci/asihpi/hpimod.c:95: error: expected â??)â?? before string constant
/usr/src/modules/alsa-driver/pci/asihpi/hpimod.c:97: error: expected â??)â?? before string constant
/usr/src/modules/alsa-driver/pci/asihpi/hpimod.c:101: error: expected â??)â?? before string constant
make[4]: *** [/usr/src/modules/alsa-driver/pci/asihpi/hpimod.o] Error 1
make[3]: *** [/usr/src/modules/alsa-driver/pci/asihpi] Error 2
make[2]: *** [/usr/src/modules/alsa-driver/pci] Error 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-server'
make: *** [compile] Error 2


I then tried to get the alsa source from the alsa project, version 1.0.11. The make crashes with the same error.
Version 1.0.13 have no problem, and 1.0.11 is also OK on gentoo. 

As a home compiled version of the alsa 1.0.13 does not work (I don't know how to replace the alsa from the source to the latest, leading to symbol problems) I wonder :

- why is the asihpi module not compiled in ubuntu ?
- how to have it working ?
- why ubuntu is released with a non compiling alsa source ? 

have anyone be able to have this sound module working ? 

Thanks.

---

