---
title: "tearing in video on second monitor"
date: 2010-05-06
forum: Multimedia Software
---

### Post by Saiph on 2010-05-06
I connect HD ready (1920x1080 at 60Hz)Samsung TV to my GeForce 9800GT through dvi cable. Xinerama enabled-disabled in nvidia config, I see tearing in every fast moving video scene. It is horisontal line which is going from up to bottom of the screen.

Using the latest nvidia drivers, ubuntu release x86. VDPAU enabled. 
How can I get clear video playback  without tearing?



**On primary monitor is all OK.** / in compiz I set 200Hz frekvency and vsync enabled

---

### Post by DGSCronos on 2010-05-08
You could try disabling compositing, worked for me. Try as root:

```
nvidia-xconfig --no-composite
```

And reboot.

---

### Post by mistermentality on 2010-05-08
I had this problem with all versions of Linux I`ve tried, with and without compiz running but found a fix on the net which finally sorted it for me.

I downloaded the compiz settings manager and set it to have a refresh rate of 60 hz and made sure sync to vblank was ticked.

Then set Nvidias driver panel to also have sync to vblank fixed.

I rebooted and the tearing was gone.

I only use my tv for output, not twinview, but have read this also solves the twinview problem.

Apparently it`s caused by the video refresh rate being rounded down so instead of say 60 hz it gets rounded down and ends up being slightly off what it should. Something like that.

---

