---
title: "glxgear comparison on older laptop noveau vs nvidia, what to use?"
date: 2013-05-07
forum: Multimedia Software
---

### Post by sdowney717 on 2013-05-07
the free noveau driver gives much better numbers
laptop has go 6150 nvidia chip

i also tried current driver and get same as 173 driver
so what should i do?

```
noveau driver

dv9000@dv9000-HP-Pavilion-dv9000-EZ452UA-ABA:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
574 frames in 5.0 seconds = 114.613 FPS
599 frames in 5.0 seconds = 119.748 FPS
577 frames in 5.0 seconds = 115.285 FPS
580 frames in 5.0 seconds = 115.836 FPS
531 frames in 5.0 seconds = 106.153 FPS
534 frames in 5.0 seconds = 106.559 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 10779 requests (10779 known processed) with 0 events remaining.
dv9000@dv9000-HP-Pavilion-dv9000-EZ452UA-ABA:~$ 

173 driver
dv9000@dv9000-HP-Pavilion-dv9000-EZ452UA-ABA:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
300 frames in 5.0 seconds = 59.907 FPS
302 frames in 5.0 seconds = 60.214 FPS
302 frames in 5.0 seconds = 60.213 FPS
299 frames in 5.0 seconds = 59.615 FPS
301 frames in 5.0 seconds = 60.005 FPS
299 frames in 5.0 seconds = 59.612 FPS
XIO:  fatal IO error 22 (Invalid argument) on X server ":0"
      after 43 requests (43 known processed) with 0 events remaining.
dv9000@dv9000-HP-Pavilion-dv9000-EZ452UA-ABA:~$ glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4

```

---

### Post by sdowney717 on 2013-05-08
there is a wglgears program for win32
I ran it and get the same results when compared to the NVidia driver in Ubuntu as to the NVidia driver in win7

there is however a big diff in how well video plays in win7 vs Ubuntu

[http://www2.cs.uidaho.edu/~jeffery/win32/](http://www2.cs.uidaho.edu/~jeffery/win32/)

---

### Post by pme 72 on 2013-05-08
The glxgears numbers for your Nvidia driver are capped at your monitor's refresh rate so you may not have a valid comparison. Not sure why the Nouveau numbers are not similarly capped as they are also supposed to be running syncronized to the vertical refresh rate.

---

