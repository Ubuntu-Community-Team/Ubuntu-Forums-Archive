---
title: "Glxgears, screensaver, Stuttering"
date: 2006-09-10
forum: Multimedia &amp; Video
---

### Post by starorbs on 2006-09-10
Hey, I've been using Ubuntu for a few days now, not a total newbie but still new.  Anyway I got everything working except this one problem. I installed the ati drivers from the repository and they worked. Glxgears gets about 4500-6000 on its default size and about 450-600 when its maximized. 
Anyway onto the problem, when I have the glxgears on full screen the graphics are stuttering, jerky whatever it may be called. Also when I have 3d screensaver on it stutters a lot. (The SS is called Hufo's Tunnel.) Seems like anything that is maximized or full screen it begins to stutter. I also tried fgl_glxgears which is guess is ATI's version of glxgears. It gets about 440-800 fps on its default size. Anyway here's some information. 

fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600 Generic
OpenGL version string: 2.0.5814 (8.25.18)
```
lsmod
```
agpgart                34888  2 fglrx,intel_agp

```

I'm still rather new so I don't know all the commands of information that may pertain to this problem.

---

### Post by frogotronic on 2006-11-09
Hi,

Had a similiar problem.  BUT, I got it when I did a fresh install of Dapper Drake.  My previous install of Dapper had no problems.  Thus, I suspected the video driver.

I am using the nVIDIA driver, but I removed the driver completely (after stopping the GDM) and then re-installed the driver.

Now everything works ok.  I guess the nVidia driver didn't quite install correctly.

Uninstalling, purging, and then reinstalling cured the problem.

-CH

---

