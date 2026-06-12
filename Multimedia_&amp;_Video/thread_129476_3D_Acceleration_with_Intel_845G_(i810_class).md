---
title: "3D Acceleration with Intel 845G (i810 class)"
date: 2006-02-13
forum: Multimedia &amp; Video
---

### Post by MooCow on 2006-02-13
Hi:
I have an Dell Inspiron 2400 with 2.4 GHz Pentium 4/768MB RAM/40GB HDD/Intel 845G onboard graphics thingy. :D 
I got Ubuntu Breezy to install, and I've been using it happily for the last few months. The problem I had recently was that when I was trying Cedega (playing around, not really for any reason. I use wine now anyways), it said I didn't have hardware acceleration. I did glxinfo and got
```
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 845G 20050225
OpenGL version string: 1.3 Mesa 6.3.2
```
which I am told is a software driver. Then I tested glxgears -printfps which told me 
```
3094 frames in 5.0 seconds = 618.732 FPS
```
Which, according to google, means I probably do have hardware acceleration. I tried to install the Intel drivers, but it didn't work, and found [http://ubuntuforums.org/showthread.php?t=97317](http://ubuntuforums.org/showthread.php?t=97317) which said the Intel drivers would be worse than the xserver ones on my computer right now. And yes, dri, glx, GLCore are all loaded in my config file (obviously). So is there hardware acceleration on my computer and if not, how can I configure it to get it? It worked on Windows for all of my games, I'm sure I can wine Counter-Strike here...

Thanks,
XO

---

