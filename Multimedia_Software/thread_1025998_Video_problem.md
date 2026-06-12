---
title: "Video problem"
date: 2008-12-30
forum: Multimedia Software
---

### Post by 1200lle on 2008-12-30
I have a video problem which makes it impossible to watch any videos in Ubuntu. The video screen turns black all the time. Additionally the drop-down menus disappear when they appear over the screen. This happens in MPlayer, Totem as well as VLC and for both video files and DVD:s. However, flash videos is not a problem. Maybe this is due to lower resolution.

To illustrate the problem I have uploaded the following video at youtube:
[http://www.youtube.com/watch?v=zCuBaE7eqgA](http://www.youtube.com/watch?v=zCuBaE7eqgA)

Notice how the screen twinkle in black and how the drop-down menus disappear.

I am new to Ubuntu and 8.10 is the only version I have used.
i did not have this problem in Vista. 

I have 4 GB of ram so performance should not be a problem.
My hardware is listed in the attached file.

I would appreciate a lot if someone could try to help me, I don't want to return to Vista.

---

### Post by xc3RnbFO8P on 2008-12-30
Try this:
> Type gstreamer-properties in terminal (Applications > Accessories in Ubuntu) and go to the video tab. Under Default Output, choose X Window System (no Xv).

---

### Post by 1200lle on 2008-12-30
Thank you sooooooo much, that helped!!!!

:D:D:D:D:D:D:D:D!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by xc3RnbFO8P on 2008-12-30
.

---

### Post by 1200lle on 2008-12-31
Thanks for the help. Unfortunately I have two other videoproblems:
1. It seems like the screen not is updated fast enough. The picture freezes for a split second all the time. This makes it impossible to watch videos where "things happens fast". 

2. (less important) The volume is way lower than it used to be when I used Vista.

Does anyone know anout any setting that could affect this?
Thanks in advance!

---

### Post by xc3RnbFO8P on 2008-12-31
Your computer spec?
Did you check if you can install Video card driver
in System> Administration> Hardware Drivers ?

---

### Post by 1200lle on 2008-12-31
I am using ATI/AMD propietary driver. All drivers that appear in "Hardware drivers" are activated. 
Please find hardware spec attached.

Thanks for trying to help!!!

---

### Post by Mad Scientist75 on 2008-12-31
Have you tried EnvyNG?

I have an ATI card that only had mediocre performance before trying Envy.  Using Envy is way easier than trying to manually install the drivers yourself.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

It did wonders for me.  Hope it helps. :D

---

### Post by xc3RnbFO8P on 2008-12-31
Here seems to solution for the sound:
[http://guide.ubuntuforums.org/showthread.php?t=992719&page=3]("http://guide.ubuntuforums.org/showthread.php?t=992719&page=3")

The screen problem could be a bug, maybe report it.

[http://www.linlap.com/wiki/acer+aspire+5530]("http://www.linlap.com/wiki/acer+aspire+5530")

---

