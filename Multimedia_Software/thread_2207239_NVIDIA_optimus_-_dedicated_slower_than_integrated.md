---
title: "NVIDIA optimus - dedicated slower than integrated"
date: 2014-02-22
forum: Multimedia Software
---

### Post by zomgwhat on 2014-02-22
Hi, 
   I've set up my toshiba laptop, which has an NVIDIA 740M GT graphics card, with ubuntu. It has optimus technology, which is intended to be used when there's a need for it. It works pretty well and I can use optirun to utilise the nvidia card: 

```

me@me-laptop:~/Desktop$ glxinfo | grep "renderer string"
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
me@me-laptop:~/Desktop$ optirun glxinfo | grep "renderer string"
OpenGL renderer string: GeForce GT 740M/PCIe/SSE2

```

I have xubuntu 13.10. I've used the x-edgers PPA to have packages for the latest video drivers: for nvidia the drivers are 331.38, xserver-nouveau and bumblebee are both up to date.

The problem is that when benchmarking, the integrated card far out performs the dedicated card which is performing very slowly. I can benchmark with glmark2 using the commands 

```

vblank_mode=0 glmark2 
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) Ivybridge Mobile 
    GL_VERSION:    3.0 Mesa 10.2.0-devel
=======================================================

...

=======================================================
                                  glmark2 Score: 1932 
=======================================================

```

```

vblank_mode=0 optirun glmark2 

=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GT 740M/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 331.38
=======================================================

...

=======================================================
                                  glmark2 Score: 520 
=======================================================

```

The vblank_mode was necccessary to stop the frame being capped at 60 FPS (my refresh rate). The nvidia card has a much lower score and of course the FPS was a lot slower, normally around 500 FPS whereas the intel card reported getting ~2000 FPS. 

What gives? That's the reverse to what I was expecting. Any ideas?

---

### Post by Yellow Pasque on 2014-02-22
Try turning off the compositing (settings -> window manager tweaks) and running tests again.

---

### Post by zomgwhat on 2014-02-22
> **Temüjin said:**
> Try turning off the compositing (settings -> window manager tweaks) and running tests again.

Hi temujin, thanks for the suggestion but it didn't have much affect on the score/FPS. Example output during tests: 

```

[texture] texture-filter=linear:ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
 FPS: 565 FrameTime: 1.770 ms
** GLX does not support GLX_EXT_swap_control or GLX_MESA_swap_control!
** Failed to set swap interval. Results may be bounded above by refresh rate.

```

Any other ideas?


***edit: apparently the slower results is the overhead from the nvidia card computing the data and then buffering it back over to intel card, and it's quite a simple scene. having benchmarked some more complex scenes the nvidia card performs normally about 30% faster (still not massively better but oh well)

---

