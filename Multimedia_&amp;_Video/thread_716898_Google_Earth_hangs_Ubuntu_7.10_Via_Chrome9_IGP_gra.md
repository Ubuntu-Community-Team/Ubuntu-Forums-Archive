---
title: "Google Earth hangs Ubuntu 7.10 Via Chrome9 IGP graphics"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by wordz2u on 2008-03-06
I recently installed a Via P4M900 chipset with its Integrated Graphics
Processor (IGP) motherboard. I am running the latest google earth for
Linux, on Ubuntu 7.10 on a Pentium Core 2 Duo processor. The Via has
an Integrated VIA Chrome9(tm) HC IGP graphic processor chip.

When I start google earth in a terminal, it hangs on the splash
screen, and gives the following error message:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libGL error: XF86DRIQueryDirectRenderingCapable failed

When I run
export LIBGL_DEBUG=verbose
glxinfo |grep direct I get

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libGL error: XF86DRIQueryDirectRenderingCapable failed
direct rendering: No (If you want to find out why, try setting
LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

When I run xvinfo I get

X-Video Extension version 2.2
screen #0
 no adaptors present

Could someone help me please to:

1. Get Google Earth to work, even if it is in simulation mode

2. Resolve the issue (which is probably due to video card setting/
configuration)

3. Advise how I can probe to find out more useful information.

Thanks.

---

