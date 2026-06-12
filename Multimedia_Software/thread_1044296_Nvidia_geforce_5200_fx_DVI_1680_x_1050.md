---
title: "Nvidia geforce 5200 fx DVI 1680 x 1050"
date: 2009-01-19
forum: Multimedia Software
---

### Post by mat429 on 2009-01-19
Hi,

after a bit of messing a looking through the forums, i eventually managed to get 1680 x 1050 through my DVI cable ( analogue works ok).  however, the problem is that it displays for a maximum of about 1 second before cutting out again - as though the signal is lost completely. Then approximately 2 seconds later, comes back on again. Then repeats.
if i move the mouse it cuts out sooner.
i have found instances on forums of people using this graphics card working at this resolution with DVI.
What would be the probable cause of this and is there any way around it?

Thanks

Mat

---

### Post by FrostDust on 2009-01-20
Is your monitor rated to use this resolution?

---

### Post by mat429 on 2009-01-20
Sorry - should ahve pointed this out 
1680 x 1050 @60Hz is the monitors rated resolution.

Thanks

Mat

---

### Post by bigbudz on 2009-05-31
Hi, what driver are you using? 

I have the same card (nvidia GeForce 5200), use the nvidia 173 driver and have a very simaler problem - wrong resolution through the DVI cable. 

VGA outputs native 1920x1080 resolution no problems.  (well except for screwing up the second display resolution , but one problem at a time). DVI outputs 1024x768 maximum resolution and is stretched across the screen. 

I tried alot of things to get the DVI working. A fresh install didn't work. 1920x1080 resolution isn't available in nvidia-settings. Tried adding a modeline in xorg.conf without success. Changed display type from CRT to DFP in xorg.conf, no dice either. 

Has anyone got the GeForce 5200 working with a DVI cable? If anyone did please let me know what driver you used or please post your xorg.conf.

---

### Post by jtappin on 2009-07-23
I think my test bed box has a 5200 (it's certainly one that recommends the 173 drivers), and a 1680x1050 monitor. The nearest resolution I've ever had with the nvidia drivers on any distro is 1600x1024 (some only manage 1440x900). I even tried manually adding a modeline to xorg.conf (obtained from the Arch Linux website) but it was ignored.

Generally the nv drivers seem OK, with the exception of one distro (not *buntu) that would do no better than 1280x800.

---

### Post by yanaek on 2009-11-30
still same problem here
[http://ubuntuforums.org/showthread.php?t=1332846](http://ubuntuforums.org/showthread.php?t=1332846)

EDIT:
not a bug, just a limitation of the GeForce FX series:
[http://www.nvidia.com/page/pg_20040109440047.html](http://www.nvidia.com/page/pg_20040109440047.html)
> 
DVI support for compatibility with nextgeneration flat panel displays with resolutions up to and including 1600×1200


---

