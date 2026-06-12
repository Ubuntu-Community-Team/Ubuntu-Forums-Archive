---
title: "fgl_glrxgears works great, but choppy screen saver?"
date: 2006-07-18
forum: Multimedia &amp; Video
---

### Post by montag451 on 2006-07-18
Hey all,

I'm running an Acer TravelMate 8204 laptop with an ATI Mobility Radeon X1600 using the 8.26 fglrx driver. When I run fgl_glxgears to test, I get some pretty good results:
```

matt@lucca:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
3708 frames in 5.0 seconds = 741.600 FPS
4347 frames in 5.0 seconds = 869.400 FPS
4341 frames in 5.0 seconds = 868.200 FPS
4337 frames in 5.0 seconds = 867.400 FPS

```
However, when I run a screen saver I get a very, very low framerate. It seems most obvious with the Latices screensaver, although it's also apparent with the less-complex GLMatrix screensaver.

Any ideas on what might be causing this? Thanks.

**Edit:** The result of fglrxinfo follows:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600 Generic
OpenGL version string: 2.0.5879 (8.26.18)

```

---

### Post by montag451 on 2006-07-20
Is this a result of the fglrx driver and its pension for crappiness, or is there something I can change that might help out my screensaver?

---

