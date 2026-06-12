---
title: "Bad tearing in OpenArena only with fullscreen mode"
date: 2014-02-05
forum: Multimedia Software
---

### Post by james-auble2 on 2014-02-05
Running OA 0.8.8-9 on Ubuntu 13.10 Xfce using Compton compositor. Windowed  mode looks great but in fullscreen mode i have bad horizontal tearing. 

lspci | grep VGA:
```


00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)


```
inxi -G:
```

Graphics:  Card: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller 
           X.Org: 1.14.5 drivers: intel (unloaded: fbdev,vesa) Resolution: 1360x768@60.0hz 
           GLX Renderer: Mesa DRI Intel Ivybridge Desktop x86/MMX/SSE2 GLX Version: 3.0 Mesa 9.2.1


```
Running  the same version of OA on my other system with same distro and settings  doesn't have this problem (although I can't get fullscreen to use the  margins on that system yet.)

Any suggestions? thanks!

---

### Post by tgalati4 on 2014-02-05
On-board graphics are OK for 2D desktops.  Less OK for 3D games.  Find a better graphics card.

---

### Post by james-auble2 on 2014-02-05
I figured my hardware might not be good enough, but why is the performance in windowed mode so good then?

---

### Post by tgalati4 on 2014-02-05
When I tried to run OpenArena on older hardware, I turned off the compositor and that helped.  My guess is that the compositor is doing a good job, but the fullscreen framebuffer mode is slow when addressing full resolution.  Understand that small increases in resolution means pixels^2 in processing.  So you can run the game in 800x600 resolution and display it on 1920x1080 but it looks blocky.  Running it at full resolution takes a lot of processing power--perhaps more than your system can handle.

If you run *phoronix-test-suite*, there are several game/graphics tests that you can run and the results will be automatically uploaded to a server so you can compare your machine with others in the database.  That will quickly answer the question "Is it just me?".

---

### Post by james-auble2 on 2014-02-05
I thought for sure I had tried this already, but changing to "Fastest" graphics settings really reduced tearing. The graphics still look decent enough for me. Turning the compositor on/off didn't seem to make much of a difference so i'll just leave it on when I play. Anyway, Thanks and i'll mark the thread solved.

---

