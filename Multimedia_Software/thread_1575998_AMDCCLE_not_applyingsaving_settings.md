---
title: "AMDCCLE not applying/saving settings"
date: 2010-09-16
forum: Multimedia Software
---

### Post by Firgeis on 2010-09-16
System:

Ubuntu 10.04  FGLRX driver

ATI Radeon HD 5670

DVI -> Samsung 23'

HDMI -> Sony Bravia 40'

After some settings juggling and restart I managed to make xorg recognize and clone the monitors. Problem is I need to change the "Pixel Format" from Yb to RGB in AMDCCCLE for the DTV (Sony), but as soon as I apply the settings it reverts back to its default value.

Even if i manually edit the /etc/ati/amdpcsdb, (the value I modifiy is DFP_AddHDTVPixelFormats) it also reverts back as soon as I restart or even re open AMDCCCLE.

---

