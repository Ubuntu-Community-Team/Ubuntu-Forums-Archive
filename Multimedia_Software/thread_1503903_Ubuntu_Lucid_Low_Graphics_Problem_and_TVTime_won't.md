---
title: "Ubuntu Lucid Low Graphics Problem and TVTime won't launch"
date: 2010-06-07
forum: Multimedia Software
---

### Post by joni8.10 on 2010-06-07
Hi everyone,

After installing Ubuntu 10.04 LTS over the weekend I had some problems, which I subsequently solved and thought I'd mention here in case anyone else is as frustrated with this as I was.

First, the dreaded Low Graphics (EE)NOUVEAU(0):Error allocating scanout buffer:-12 which wouldn't allow me to change my monitor resolution. 

Second, TVTime television viewer would not launch at all.

Solution to BOTH of these problems:

From Synaptic uninstall xserver-xorg-video-nouveau(experimental) and reinstall xserver-xorg-video-nv.

Now everything works! :cool:

---

### Post by manolomanolo on 2010-07-08
Thanks. It worked for me!

---

### Post by manolomanolo on 2010-07-14
Unfortunately the problem has not been solved.
I removed the nouveau drivers and actually the initial error message disappeared. But playing video on youtube is very very hard. The video is not fluent.

Any siggestion, please?
thanks.

PD: the video was fluent in Karmik. Upgrading to Lucid caused the problem. Installing Lucid from scratch did not help.

---

### Post by wlraider70 on 2010-07-17
youtube issues are often caused by flash.
Flash does NOT play nice with linux.

try a different video source to test your card.

---

### Post by wlraider70 on 2010-07-18
youtube issues are often caused by flash.
Flash does NOT play nice with linux.

try a different video source to test your card.

---

