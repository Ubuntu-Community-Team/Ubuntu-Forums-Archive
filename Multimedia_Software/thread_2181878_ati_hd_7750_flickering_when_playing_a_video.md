---
title: "ati hd 7750 flickering when playing a video"
date: 2013-10-19
forum: Multimedia Software
---

### Post by eayin on 2013-10-19
Since a few weeks when I watch a video (tried vlc, kaffeine, mplayer) a horizontal line in always the same spot is flickering. Iam using the "radeon" driver for my graphic card ati hd 7750.  The driver package is already preinstalled on ubuntu (xserver-xorg-video-ati). I have ubuntu 13.10 installed. I can exclude a hardware issue, because if I boot the same system in windows I don't have the flickering issue. If I pause the video I never see the flickering. It is only seen when playing the video. In calm video scenes there is also no flickering to be seen. This is my xorg.0.log [http://ix.io/8BP](http://ix.io/8BP)

---

### Post by eayin on 2013-10-27
I switched to the proprietary ati graphic card drivers (fglrx) and with flgrx the vertical tearing is gone and the overall graphic looks better, but now I get occasionally segfaults when I maximize a window with a shortcut to the right or left side of the screen.
I remember having the same issue with the segfaults and the proprietary driver fglrx in 2012 with arch. Switching to ubuntu and using the radeon driver
solved the segfault issue. 

Would you recommend to uninstall fglrx and try to go with the current ati catalyst driver from ati's website directly? 
([AMD Catalyst&#8482; 13.4 Proprietary Linux x86 Display Driver]("http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-13-4-linux-x86.x86_64.zip"))

Or maybe even the Beta from ati's website: [Latest Beta Driver]("http://www2.ati.com/drivers/beta/amd-catalyst-13.11-beta6-linux-x86.x86_64.zip") ?

---

