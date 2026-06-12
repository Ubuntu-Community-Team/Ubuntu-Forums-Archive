---
title: "wireless stopped working after upgrading kernel ubuntu 10.04 LTS"
date: 2011-11-10
forum: Networking &amp; Wireless
---

### Post by tuxt on 2011-11-10
Hello everyone :)

Have been experience some problem after I did an upgrade to kernel 2.6.32-35,
on a Toshiba Satellite C660 64-bit.

Am using Ubuntu 10.04.3, 32-bits version.

The problem is that the wireless seems to stop working after the upgrade :(

On the old kernel, I downloaded the correct driver, and installed build-essentials, and the correct linux-headers for that kernel.

Here is the output I got when trying to install the driver again:

skeletor@skeletor-laptop:~/rtl8192ce_linux_2.6.0006.0321.2011$ sudo make
 [sudo] password for skeletor:  

 make[1]: Går till katalogen "/usr/src/linux-headers-2.6.32-35-generic"
   Building modules, stage 2.
   MODPOST 1 modules
   CC      /home/skeletor/rtl8192ce_linux_2.6.0006.0321.2011/HAL/rtl8192/r8192ce_pci.mod.o
   LD [M]  /home/skeletor/rtl8192ce_linux_2.6.0006.0321.2011/HAL/rtl8192/r8192ce_pci.ko
 make[1]: Lämnar katalogen "/usr/src/linux-headers-2.6.32-35-generic"


 skeletor@skeletor-laptop:~/rtl8192ce_linux_2.6.0006.0321.2011$ sudo make install

 make[1]: Går till katalogen "/usr/src/linux-headers-2.6.32-35-generic"
   Building modules, stage 2.
   MODPOST 1 modules
 make[1]: Lämnar katalogen "/usr/src/linux-headers-2.6.32-35-generic"
 make[1]: Går till katalogen "/home/skeletor/rtl8192ce_linux_2.6.0006.0321.2011/HAL/rtl8192"
 make -C /lib/modules/2.6.32-35-generic/build M= CC=gcc modules
 make[2]: Går till katalogen "/usr/src/linux-headers-2.6.32-35-generic"
   CHK     include/linux/version.h
   CHK     include/linux/utsrelease.h
   SYMLINK include/asm -> include/asm-x86
 make[3]: *** Ingen regel för att skapa målet "kernel/bounds.c", som behövs till "kernel/bounds.s".  Stannar.
 make[2]: *** [prepare0] Fel 2
 make[2]: Lämnar katalogen "/usr/src/linux-headers-2.6.32-35-generic"
 make[1]: *** [modules] Fel 2
 make[1]: Lämnar katalogen "/home/skeletor/rtl8192ce_linux_2.6.0006.0321.2011/HAL/rtl8192"
 make: *** [install] Fel 2
 

Help needed badly?

Please :)

---

