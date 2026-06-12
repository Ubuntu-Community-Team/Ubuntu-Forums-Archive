---
title: "8400gs no vga signal?"
date: 2011-08-23
forum: Multimedia Software
---

### Post by Mastus on 2011-08-23
Hi,

This is probably a hardware thing, but I'm just interested if someone has noticed the same thing.

64bit system, Ubuntu 10.04, 8400gs (g86 core), nvidia driver 275.09.07

I have a 19" CRT monitor (yeah... I know, should buy a new monitor) connected via VGA and on the DVI port I have a DVI->HDMI adapter which is connected to a 42" LCD TV.

Everything works fine - DVI is outputting 1920x1080 resolution, vdpau works, and VGA monitor uses 1280x1024 resolution. 

Except when you decide to boot your computer. Monitor stays blank the whole time (no signal whatsoever) and the LCD TV is showing the post screens and ubuntu login screens. When in this state I run nvidia-settings and try to detect displays - none other than the TV is found. Hence no signal to monitor.

When you unplug the HDMI cable and reboot, monitor wakes up as it should. When in desktop, you reconnect the HDMI cable and detect displays -> TV is detected and all is well again.

Has anyone had this kind of behaviour before?

---

