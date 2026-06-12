---
title: "2 AMD/ATI cards, 3 monitors"
date: 2013-10-21
forum: Multimedia Software
---

### Post by bluesimage on 2013-10-21
$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Turks PRO [Radeon HD 6570/7570]
04:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430]

One monitor is VGA only, it is plugged into VGA port on the 6570 and another monitor is plugged into same card on DVI port. Both work fine.

Third monitor is plugged in via DVI port on newly installed 5430 card. Best I can get it is a white screen with a black X pointer - before screen turns white on that monitor I can actually see the wallpaper on it for a couple seconds. 

Using latest proprietary amd drivers. I've tried about every combination of Xorg.conf I can think of - If anyone has multiple ATI/AMD cards for 3 monitors, can you please offer some advice? If anyone has VGA+DVI on one, and DVI on the third (or something close) could I please see relevant Xorg.conf?

---

