---
title: "Can not get hardware-accelerated 3D to work with ATi Radeon 9600 Pro"
date: 2005-11-03
forum: Multimedia &amp; Video
---

### Post by Pettman on 2005-11-03
As the title indicates I have troubles with geting the hardware accelerated #D rendering to work, when running glxgears or planetpenguin-racer (the only programs I have tested so far) the program runs smoothly for 1 or 2 seconds and then everything starts lagging like hell. When I run glxgears -printfps I get the following output ```
1907 frames in 5.1 seconds = 370.736 FPS
3240 frames in 5.2 seconds = 620.706 FPS
1560 frames in 5.0 seconds = 310.708 FPS

```It seems that it is just the 3D stuff that laggs, the rest of the system is just fine.
The fglrxinfo command gives the following output
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```
I have attached the output from glxinfo

---

### Post by Cuppa-Chino on 2005-11-03
please check the following threads:

[ATI: Install the included 8.16.20 fglrx driver]("http://ubuntuforums.org/showthread.php?p=408111")

[ATI: Install the newer 8.18.8 fglrx driver]("http://ubuntuforums.org/showthread.php?t=78466")

and then check this thread:
[stuborn fglrx module does not want to load, driver 8.18 ATI Mobility 9700SE]("http://ubuntuforums.org/showthread.php?t=80215")

---

### Post by Pettman on 2005-11-03
Had already cheked the two first guides, they did not help. The third one I had seen, but I will try its solution.

---

