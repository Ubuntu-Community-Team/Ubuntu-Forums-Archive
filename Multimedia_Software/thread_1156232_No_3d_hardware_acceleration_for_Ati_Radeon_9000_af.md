---
title: "No 3d hardware acceleration for Ati Radeon 9000 after upgrading 8.10-&gt;9.04"
date: 2009-05-11
forum: Multimedia Software
---

### Post by portero on 2009-05-11
Hi,

I upgraded from 8.10 to 9.04 and unfortunately the first thing I noticed after the upgrade was the sluggishness of the desktop. I found some tweaks for xorg.conf which helped a bit but I could not get 3d hardware acceleration to work. The flash videos are still flickering and I can live with it but I really would have use for 3d hardware acceleration.

glxinfo confirms that 3d rendering is not accelerated.

$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Software Rasterizer

The following Xorg.0.log lines may be relevant:

(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0

I'll attach xorg.conf and Xorg.0.log

Any ideas? Thanks,
Tero

---

