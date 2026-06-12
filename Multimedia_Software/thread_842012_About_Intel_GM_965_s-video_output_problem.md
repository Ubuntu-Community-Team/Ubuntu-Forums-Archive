---
title: "About Intel GM 965 s-video output problem"
date: 2008-06-26
forum: Multimedia Software
---

### Post by super_hill on 2008-06-26
I have a aopen MP965-DR mini-PC, and the system is Ubuntu 8.04 hardy, after I update the xserver-xorg-video-intel driver to 2:2.3.2, I can show the screen on TV through s-video cable.

But the  initiate screen is hue(black and white), after using xrandr to set TV_FORMAT to NTSC-443, the screen get the color, but too bright and seems some color have lost.

I tried to add the DefaultDepth 24 in xorg.conf, but still not work after reboot.

Could someone can help me?

---

### Post by super_hill on 2008-06-30
The color problem have been solved of mini-PC, what I did is:
-------------------------------------------------------------------------------------
1. Get the latest intel GM965 driver source code "xf86-video-intel" from: [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)
2. modify RGB parameters in i830_tv.c
3. Build and install the latest driver according to: [http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)

Than it works, and the color can accord with your requirement.

---

