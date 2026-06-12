---
title: "Broadcom BCM 70012 Ubuntu 13.04"
date: 2013-05-23
forum: Multimedia Software
---

### Post by mmisbg on 2013-05-23
I'm wondering if anybody else has had any luck getting a Broadcom BCM 70012 Crystal HD card to work with Ubuntu 13.04.

I have installed the card on an Acer AOD250, and it works with my WinXP partition, but I cannot seem to get the card to work with my Ubuntu partition.

This stinks, because I'm debating getting a SSD as my next upgrade, and ditching windows for good.

I've followed the instructions on the following two websites:

[http://knowledge.evot.biz/documentation/how-to-compile-and-install-the-broadcom-crystal-hd-hardware-decoder-bcm70012-70015-driver-on-ubuntu](http://knowledge.evot.biz/documentation/how-to-compile-and-install-the-broadcom-crystal-hd-hardware-decoder-bcm70012-70015-driver-on-ubuntu)


[https://code.google.com/p/indicator-crystalhd/wiki/CrystalHDHowTo](https://code.google.com/p/indicator-crystalhd/wiki/CrystalHDHowTo)

Both times, I received warnings involving Linux version 3.8 during the process.

After both attempts, I lost video (still had audio when playing video, with blank video screens), and I had to perform a system reinstall in order to restore my video.  I have also installed the Broadcom plug-ins from the Software Center, but I cannot seem to verify that they are actually doing anything.

I have finally been able to see the "enable hardware acceleration" checkbox checked in the flash settings for chromium, but I can't verify that it is actually working.

Any advice would be great.  Thanks!

---

### Post by dino99 on 2013-05-23
Looks like you have to compile the driver from the source
[http://www.linuxplained.com/install-broadcom-crystal-hd-driver-ubuntu/](http://www.linuxplained.com/install-broadcom-crystal-hd-driver-ubuntu/)

---

### Post by Bucky Ball on 2013-05-23
*Thread moved to **Networking & Wireless**.*

---

### Post by mmisbg on 2013-05-23
As with the other two websites, those instructions yield the following errors:

*****@*****-laptop:~/crystalhd/driver/linux$ make
make -C /lib/modules/3.8.0-21-generic/build SUBDIRS=/home/john/crystalhd/driver/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-21-generic'
  CC [M]  /home/*****/crystalhd/driver/linux/crystalhd_lnx.o
/home/*****/crystalhd/driver/linux/crystalhd_lnx.c:434:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘chd_dec_init_chdev’
/home/*****/crystalhd/driver/linux/crystalhd_lnx.c:501:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘chd_dec_release_chdev’
/home/*****/crystalhd/driver/linux/crystalhd_lnx.c:526:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘chd_pci_reserve_mem’
/home/*****/crystalhd/driver/linux/crystalhd_lnx.c:585:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘chd_pci_release_mem’
/home/*****/crystalhd/driver/linux/crystalhd_lnx.c:600:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘chd_dec_pci_remove’
/home/*****/crystalhd/driver/linux/crystalhd_lnx.c:628:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘chd_dec_pci_probe’
/home/*****/crystalhd/driver/linux/crystalhd_lnx.c:817:14: error: ‘chd_dec_pci_probe’ undeclared here (not in a function)
/home/*****/crystalhd/driver/linux/crystalhd_lnx.c:818:2: error: implicit declaration of function ‘__devexit_p’ [-Werror=implicit-function-declaration]
/home/*****/crystalhd/driver/linux/crystalhd_lnx.c:818:26: error: ‘chd_dec_pci_remove’ undeclared here (not in a function)
/home/*****/crystalhd/driver/linux/crystalhd_lnx.c:22:22: error: ‘crystalhd_class’ defined but not used [-Werror=unused-variable]
cc1: all warnings being treated as errors
make[2]: *** [/home/*****/crystalhd/driver/linux/crystalhd_lnx.o] Error 1
make[1]: *** [_module_/home/*****/crystalhd/driver/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-21-generic'
make: *** [all] Error 2

I think this has something to do with linux 3.8.  I don't really have the know-how to be sure though.

(I'm also a little confused.  The thread was moved to "Networking & Wireless", but the card I'm attempting to configure is a Graphics Accelerator.)

---

### Post by mmisbg on 2013-05-26
I just loaded the same video on my Windows XP partition and on my Ubuntu partition.  The HD graphics accelerator is clearly working in Windows and not in Ubuntu.  I'm starting to think that there is no solution to this.  

Anybody have fresh ideas?

---

### Post by TheDBP on 2013-05-29
I've been trying to get this to work with 13.04 as well, no luck - my advice is to stick with 12.10 for now.

---

### Post by Bucky Ball on 2013-05-29
*Thread moved to **Multimedia & Video***

Apologies. My mistake. Good luck. ;)

---

### Post by mmisbg on 2013-05-29
Bucky Ball: Thank you for the correction.

TheDBP:  Thank you for confirming that this isn't just my system.  A new update came through the other day, haven't tried it since then.  However, I was thinking of reverting to 12.10 anyway.  I use MuseScore quite a bit, and version 1.3 doesn't work well in 13.04.  Aside from that, I've found the new version to be a little buggy.  I'm impressed with the performance, and the overall look of the new version, but I've had the system hang quite a bit.  I've also had programs crash while I am using them.  Seems like I should stick with the LTS version if it is to become my one an only operating system.  Thanks again!

---

### Post by TheDBP on 2013-06-14
> **mmisbg said:**
> Bucky Ball: Thank you for the correction.

TheDBP:  Thank you for confirming that this isn't just my system.  A new update came through the other day, haven't tried it since then.  However, I was thinking of reverting to 12.10 anyway.  I use MuseScore quite a bit, and version 1.3 doesn't work well in 13.04.  Aside from that, I've found the new version to be a little buggy.  I'm impressed with the performance, and the overall look of the new version, but I've had the system hang quite a bit.  I've also had programs crash while I am using them.  Seems like I should stick with the LTS version if it is to become my one an only operating system.  Thanks again!

My experience with this is on an AppleTV first gen which I use as an XBMC front-end.  I like Crystalbuntu and OpenELEC but prefer having more control over the system, run an lxde session with web browser and spotify etc.  works surprisingly well!  I wanted to move to 13.04 due to its massively improved RAM efficiency (AppleTV only has 256MB, every little bit counts), but without CrystalHD working it doesn't matter how little RAM it uses :D

Unfortunately there haven't been pre-built drivers that work for these in some time from what I gather, and because the hardware is end of life and most modern video subsystems (even on netbooks) can do HD no problem, the impetus for getting it working is not great.  I hold out hope someone will fix it (I'm certainly not knowledgable enough to do so, nor do I have the free time), but part of me thinks that 12.10 might be end of the road for CrystalHD support ... which is a shame.

---

