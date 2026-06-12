---
title: "gusty pvr350 - ivtv vs lirc"
date: 2007-12-31
forum: Mythbuntu
---

### Post by rstm on 2007-12-31
I've completed a fresh instalation of Gusty with a pvr-350 board. The system  ran fine on the regualr monitor. Then I followed the PVR-350 tv-out guide. After the xserver-xorg-video-ivtv drivers are installed, the kernel stops installing /dev/lirc0.  If I uninstall the ivtv driver the kernel will install /dev/lirc0 and everything works.   Any suggestions?

---

### Post by rstm on 2008-01-01
the instructions said "Follow the prompts to install everything.", but if I just install the ivtv drivers and don't update these other packages;

linux-ubuntu-modules-2.6.22-14-generic 
mplayer 

I get video out and the remote works.


> **rstm said:**
> I've completed a fresh instalation of Gusty with a pvr-350 board. The system  ran fine on the regualr monitor. Then I followed the PVR-350 tv-out guide. After the xserver-xorg-video-ivtv drivers are installed, the kernel stops installing /dev/lirc0.  If I uninstall the ivtv driver the kernel will install /dev/lirc0 and everything works.   Any suggestions?

---

