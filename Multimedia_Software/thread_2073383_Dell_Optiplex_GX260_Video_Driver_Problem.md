---
title: "Dell Optiplex GX260 Video Driver Problem"
date: 2012-10-19
forum: Multimedia Software
---

### Post by rahim701 on 2012-10-19
I install ubuntu on Dell Optiplex GX260 desktop. It can't detect video driver.
How can I install video driver on my computer?
I am not totally a newbie, know how to use terminal etc.
So, if you share which code i have to use, I think i can install them.
Thanx.

I tried
**glxinfo | grep OpenGL**
result:
> OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 845G x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 8.0.2
OpenGL extensions:


**cat /var/log/Xorg.0.log | grep DRI**
> [    39.666] (II) Loading extension XFree86-DRI
[    39.667] (II) Loading extension DRI2
[    41.088] (II) intel(0): [DRI2] Setup complete
[    41.088] (II) intel(0): [DRI2]   DRI driver: i915
[    41.244] (II) intel(0): direct rendering: DRI2 Enabled
[    42.018] (II) GLX: Initialized DRI2 GL provider for screen 0


---

### Post by BicyclerBoy on 2012-10-19
AFAICT That old box has on-board chipset intel graphics & an AGP slot..

Your posted info shows the correct/working intel driver.
The intel driver is free open source & built-in & supplied in *buntu.
There is nothing better.

There is a very small possibility of performance improvement & a great opportunity for trouble by using xorg-edgers ppa.
(LOTR like dialogue)

For e.g.: xorg-edgers ppa & intel 945gme:
- compix was crashing (partly broken desktop) for about 3 months.
- pasted text does not render (invisible) until changed.
In addition..the xorg-edgers ppa kernel breaks the broadcomm b43 wifi module (fixable).

---

