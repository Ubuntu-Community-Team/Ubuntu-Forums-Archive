---
title: "Tungsten Graphic Mesa DRI Intel(R) 915GM x86/MMX/SSE2 Blocked for Driver Issues"
date: 2013-02-24
forum: Multimedia Software
---

### Post by Ralph L on 2013-02-24
I have very slow graphics performance on some web sites (such as panning on this site [http://www.360cities.net/image/mars-panorama-curiosity-solar-day-177#-15.32,29.86,85.0](http://www.360cities.net/image/mars-panorama-curiosity-solar-day-177#-15.32,29.86,85.0)).  When I enter "about:support" (no quotes) in the firefox browser box I get, under Graphics:

```
Adapter Description  Tungsten Graphics, Inc -- Mesa DRI Intel(R) 915GM x86/MMX/SSE2
Device ID  Mesa DRI Intel(R) 915GM x86/MMX/SSE2
Driver Version  1.4 Mesa 8.0.4
GPU Accelerated Windows  0/3 Basic Blocked for your graphics card because of unresolved driver issues.
Vendor ID  Tungsten Graphics, Inc
WebGL Renderer  Blocked for your graphics card because of unresolved driver issues
AzureCanvasBackend  cairo
AzureContentBackend  none
AzureFallbackCanvasBackend  none
```

As I read this Firefox isn't using my hardware graphics, because it thinks there is a driver problem with it.

My computer is a Dell Latitude D610 laptop running Ubuntu 12.04.1 with Firefox 18.0.2.

Does anyone know how to fix this?  Does anybody know of an alternate driver for this graphics card?  I googled it and could find nothing.

Thanks in advance.

---

### Post by Yellow Pasque on 2013-02-25
I think you need OpenGL 2.1 or higher, but you can try forcing it on: [https://wiki.mozilla.org/Blocklisting/Blocked_Graphics_Drivers#On_X11](https://wiki.mozilla.org/Blocklisting/Blocked_Graphics_Drivers#On_X11)

---

### Post by Ralph L on 2013-02-25
Thanks for the response.  I really appreciate it.  How do I find if I have OpenGL 2.1 or higher?  Also, if I try to force it, how much damage am I likely to do?  Is there any way to recover, or will I have to do a completely new install of Ubuntu?

Thanks again

---

