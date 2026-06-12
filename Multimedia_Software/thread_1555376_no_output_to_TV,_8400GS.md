---
title: "no output to TV, 8400GS"
date: 2010-08-18
forum: Multimedia Software
---

### Post by brianmch on 2010-08-18
Hi Folks:

I just built a couple of PCs, one for routine desktop use and mythtv backend, another for a mythtv frontend.  The desktop is working pretty well, need to tweak a few things yet.

The problem is with the myth frontend box.  It has the following specs:
-Asus M2N68-AM PLUS
-Asus 8400GS silent PCIe video card
-fresh install of ubuntu 10.04
-Nvidia current proprietary drivers activated (noveau un-installed)

The video works fine with an LCD monitor thru DVI and VGA.  When I moved it to the entertainment center and hooked up the DVI-HDMI cable to the TV the video stopped working.  When I boot, the splash screen displays, then the ubuntu boot screen flashes up for a moment, then a squiggly sync thing pops up, then the display goes black.

I searched the forum for related issues, and tried adding the following to my xorg.conf:
these might not be exact, just entering here from memory...
Option "UseDisplayDevice"  "DFP"
Option "DynamicDualView"  "False"

Any suggestions?  I am pretty new to Linux (used Red Hat back in 1996/7 to write C++ code for my masters project, CADCAM related), but nothing since.

Thanks,
Brian

---

