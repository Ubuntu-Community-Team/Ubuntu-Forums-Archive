---
title: "Orinoco Patch Drivers Wont Compile"
date: 2006-02-15
forum: Networking &amp; Wireless
---

### Post by adub on 2006-02-15
# make
make -C /usr/src/linux-headers-2.6.12-10-386 M=/orinoco/orinoco-0.15rc4 KERNELRELEASE=2.6.12-10-386 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /orinoco/orinoco-0.15rc4/orinoco.o
/orinoco/orinoco-0.15rc4/orinoco.c: In function `orinoco_rx_monitor':
/orinoco/orinoco-0.15rc4/orinoco.c:724: error: storage size of 'hdr' isn't known
/orinoco/orinoco-0.15rc4/orinoco.c:724: warning: unused variable `hdr'
/orinoco/orinoco-0.15rc4/orinoco.c: At top level:
/orinoco/orinoco-0.15rc4/orinoco.c:4258: warning: 'orinoco_ioctl_setprism2header' defined but not used
/orinoco/orinoco-0.15rc4/orinoco.c:4292: warning: 'orinoco_ioctl_setfcsbytes' defined but not used
make[2]: *** [/orinoco/orinoco-0.15rc4/orinoco.o] Error 1
make[1]: *** [_module_/orinoco/orinoco-0.15rc4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2



I followed the tutorial i have build-essential and the other necessary steps of the tutorial in ubuntu forums

i have an orinoco gold classic of coarse

i have done CC=gcc-3.4 to make sure it is compiling with the right gcc

i just dont know from here??

thanks to all who reply


TRYING TO GET MONITOR MODE WORKING BTW THE DRIVERS THAT COME WITH 5.10/BREEZY GET THE CARD WORKING BUT NOT THE MONITOR MODE

---

### Post by adub on 2006-02-16
problem fixed

---

