---
title: "An ATi fglrx issue"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by usernamed on 2006-06-05
I've installed the ATi fglrx drivers (as per the how-to, not using the ATI installer)

fglrxinfo looks ok:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

but when I run fgl_glxgears:

```
$ fgl_glxgears

Using GLX_SGIX_pbuffer
Floating point exception

```

I haven't seen this particular error before, can anybody offer any advice?

---

### Post by hardhu on 2006-06-16
I have the same problem here (notebook Acer Aspire 5024 with ati radeon x700 and kubuntu dapper amd64) both installing the Dapper's Included Driver (8.25.18) and 
generating Ubuntu packages for the 8.25.18 drivers in Ubuntu Dapper manually. Maybe I will report it as a bug

---

### Post by Galban on 2006-06-16
Everything ok here!

rodolfo@amdasus:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
1556 frames in 5.0 seconds = 311.200 FPS
2381 frames in 5.0 seconds = 476.200 FPS
2353 frames in 5.0 seconds = 470.600 FPS
2379 frames in 5.0 seconds = 475.800 FPS
2384 frames in 5.0 seconds = 476.800 FPS
2350 frames in 5.0 seconds = 470.000 FPS
2375 frames in 5.0 seconds = 475.000 FPS
2378 frames in 5.0 seconds = 475.600 FPS
2336 frames in 5.0 seconds = 467.200 FPS
2294 frames in 5.0 seconds = 458.800 FPS
rodolfo@amdasus:~$


May be you guys you should give a try to this: [http://www.ubuntuforums.org/showthread.php?t=197471]("http://www.ubuntuforums.org/showthread.php?t=197471")

---

### Post by hardhu on 2006-06-19
[QUOTE=Galban]Everything ok here!

rodolfo@amdasus:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
1556 frames in 5.0 seconds = 311.200 FPS
2381 frames in 5.0 seconds = 476.200 FPS
2353 frames in 5.0 seconds = 470.600 FPS
2379 frames in 5.0 seconds = 475.800 FPS
2384 frames in 5.0 seconds = 476.800 FPS
2350 frames in 5.0 seconds = 470.000 FPS
2375 frames in 5.0 seconds = 475.000 FPS
2378 frames in 5.0 seconds = 475.600 FPS
2336 frames in 5.0 seconds = 467.200 FPS
2294 frames in 5.0 seconds = 458.800 FPS
rodolfo@amdasus:~$


May be you guys you should give a try to this: [http://www.ubuntuforums.org/showthread.php?t=197471]("http://www.ubuntuforums.org/showthread.php?t=197471")[/QUOTE]

As I can read from your link, you seem to talk about x86 ati driver, while these seem to be an x86_64 driver related problem.

---

