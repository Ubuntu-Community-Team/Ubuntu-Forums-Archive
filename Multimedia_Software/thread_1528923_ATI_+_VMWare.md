---
title: "ATI + VMWare"
date: 2010-07-11
forum: Multimedia Software
---

### Post by Pwam on 2010-07-11
Hi all,

Newly registered here, despite viewing the forum probably at least once a day for the last 6 months!  Extremely useful always.  However, I haven't been able to find the answer to this today.

I am using VMWare player to run XP pro under Ubuntu 9.10.  I have a Radeon X600 graphics card, which i have struggled with so far as getting desktop effects etc working so far.  I have now got desktop effects working, but i still do not have any 3d acceleration in VMWare player.  

glxinfo | grep vendor gives:

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project

and dmesg | grep drm gives:


[    2.253841] [drm] Initialized drm 1.1.0 20060810
[    2.273030] [drm] radeon default to kernel modesetting DISABLED.
[    2.273535] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[   23.622056] [drm] Setting GART location based on new memory map
[   23.623415] [drm] Loading R300 Microcode
[   23.623456] [drm] Num pipes: 1
[   23.623463] [drm] writeback test succeeded in 1 usecs

from what I've read so far, OpenGL vendor should be SGI rather than DRI, and the drm check should show KMS as enabled.  I have tried using the fglrx driver but that gets rid of 3D support in ubuntu too!

Anyone any ideas as to why KMS/OpenGl aren't right??

Thanks!

---

