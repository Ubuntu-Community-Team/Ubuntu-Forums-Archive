---
title: "intel 852GM graphics driver"
date: 2011-08-27
forum: Multimedia Software
---

### Post by honeycombs_big_yahyahyah on 2011-08-27
Hi Folks,

I'm trying to run xbmc on an old Toshiba A10-SP129 laptop, which has an Intel 852GM chipset.  Ubuntu 11.04 disables the Intel drivers by default, and I followed the instructions here to enable them: [https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

According to Xorg.0.log, it does seem to load: [http://pastebin.com/nLpnR01D](http://pastebin.com/nLpnR01D) .  (So that's good).

However, when I run ubuntu desktop and run glxinfo, I get the following: [http://pastebin.com/v6NhWNzh](http://pastebin.com/v6NhWNzh)  .  OpenGL (2.1) is via Mesa, and when I run glxgears, it takes about  50% of my CPU.  So - is the intel driver not working?   Shouldn't the 3D  rendering be taken over by the GPU?  Any thoughts would be greatly appreciated!

thanks!

Ubuntu Server 11.04
Xorg installed with ubuntu-desktop, GDM uninstalled
Toshiba A10-SP129, Celeron 2.4 GHz (specs: [http://www.pcenlinea.com/mp/32398.html](http://www.pcenlinea.com/mp/32398.html) )

---

### Post by BicyclerBoy on 2011-08-27
For comparison.
Using Atom 330 945GME chipset GMA900 running Unity3d 11.04.
Using intel driver from xorg-edgers launchpad ppa.
CPU hovers around 40% running glxgears.

I'm surprised how well the weak intel machine works.
It can run MythTV & playback **SD** H264..
The CPU must be doing the video decode (openGL only used for GUI, DRI2 used for video rendering)

from glxinfo
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GME x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.12-devel

---

### Post by .... on 2011-08-27
Try this to see why software rasterizing is used:
```
LIBGL_DEBUG=verbose glxinfo
```

---

