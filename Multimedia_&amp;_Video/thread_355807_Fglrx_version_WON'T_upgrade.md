---
title: "Fglrx version WON'T upgrade"
date: 2007-02-07
forum: Multimedia &amp; Video
---

### Post by jaywhy13 on 2007-02-07
Have a look at "cat /var/log/Xorg.0.log | grep fglrx"

I'll highlight the line that I do believe is giving the trouble

(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x6000
(II) fglrx(0): [drm] mapped SAREA 0x6000 to 0xb70ec000
(II) fglrx(0): [drm] framebuffer handle = 0x7000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
[COLOR="Red"]**(II) fglrx(0):     Version: 8.28.8**[/COLOR]
(II) fglrx(0):     Date: Aug 17 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[COLOR="Red"][B](WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
[/B][/COLOR](II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x6000 at 0xb70ec000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

I have version 8.32 from ati's site. I've tried to install that TOOOO many times and that verion that shows up won't change!!!!! Any ideas why?

Kubuntu also installed the WRONG kernel version for my kernel... it installed a generic one instead of installing the 386. I went ahead and got the kernel image, headers and restricted modules for 386 and I am using that kernel version now but cannot resolve my system's apparent obsession with the old driver. 

PLEASE HELP

---

### Post by jaywhy13 on 2007-02-07
Ok... fixed that one by doing cat /lib/modules/modules.dep | grep fglrx and deleting all the agpkart.ko files that that query returned.

Now I've got a slightly lessened error.... have a look
The dreaded "message" 
[COLOR="Red"]**(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0**[/COLOR]

which leads to:

==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.1.0
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection for driver fglrx.
(EE) fglrx(0): Failed to initialize GPS!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

Had this problem before.. NO CLUE how I solved it

---

### Post by jaywhy13 on 2007-02-07
Anyone kno how 2 solve this one?

---

