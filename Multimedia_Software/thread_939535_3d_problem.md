---
title: "3d problem"
date: 2008-10-06
forum: Multimedia Software
---

### Post by deunnero on 2008-10-06
Problem.  I need to figure out howto initialize 3d 

Card:  Ati radeon xpress 200m

Steps I have taken; 
Removed the proprietary driver.
Installed Edgy  (installed ati drivers for me =] )

However with both the proprietary driver it still doesn't support 3d for some reason

Some debug stuff (don't know if it will help?)

jonathan@jonathan-laptop:~$ glxgears
Segmentation fault

jonathan@jonathan-laptop:~$ glxinfo
name of display: :0.0
Segmentation fault

jonathan@jonathan-laptop:~$ glxinfo
name of display: :0.0
Segmentation fault


Thanks,
Jon

---

### Post by ea1475 on 2008-10-15
I'm having this same problem.

---

### Post by BMWDriver on 2008-10-15
Visit the [Unofficial ATI Driver Wiki]("http://www.wiki.cchtml.com/") where you will be able to find a lot of useful information on installing the ATI drivers, troubleshooting and verifying of the install. The site is superbly organized, I found.

I had the same headaches as you guys, and found the cure up there.

Once you get the driver running properly, you will want to visit the configuring section of the Wiki and enable 2D acceleration. This way you will be able to have great video playback, especially when going in full screen mode.

Good luck !

---

