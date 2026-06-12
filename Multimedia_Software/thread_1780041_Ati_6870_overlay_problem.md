---
title: "Ati 6870 overlay problem"
date: 2011-06-11
forum: Multimedia Software
---

### Post by zard_cz on 2011-06-11
Hi,
I have recently installed the latest Ubuntu 11.04 and I have a problem with overlay. 
Basically, any OpenGL-related content (accelerated video through VLC, OpenGL based games (Chromium BSU), etc.) all show black frame where the picture should have been. But if I open another application and drag it over the original window, it does seem to show the picture, albeit quite flickery.

I have temporarily solved it via redirecting output of VLC to the X11 renderer but for some of the application it is not possible.

My graphics card is ATI 6870 and I am using the latest binary driver installed from their site. OpenCL works fine, fglrxinfo gives me following info:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6800 Series
OpenGL version string: 4.1.10750 Compatibility Profile Context

I am also running binary Nvidia driver at the same time to use CUDA on my Tesla card (C1060, no monitors supported) and that also works fine.

Also, all the normal graphical bits seem to work fine - dual monitor support works fine with full resolution.

Is there any other info I should provide?

Thank you very much

---

