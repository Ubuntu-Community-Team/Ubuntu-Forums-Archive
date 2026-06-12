---
title: "Resolution problem for TFT"
date: 2005-11-25
forum: Multimedia &amp; Video
---

### Post by kbroodco on 2005-11-25
I have a HP L1520 TFT 15" monitor and a Asus V9520MAGIC/T recognized as a Geforce Fx5200(which it is). 

The problem is: I cannot set my resolution to 1024x768. The screen gives me an out of range. Smaller and bigger is no problem, just those settings (the recommended settings for my tft) don't work.

I have installed the nvidia drivers according to the Ubuntu Quick Guide. In the Nvidia settings the monitor is defined as a CRT1.

Does anybody know how to fix this?

---

### Post by Burkey on 2005-11-25
check out

[http://www.ubuntuforums.org/showthread.php?t=88876&highlight=horizsync](http://www.ubuntuforums.org/showthread.php?t=88876&highlight=horizsync)

might help

---

### Post by teaker1s on 2005-11-25
sudo dpkg-reconfigure xserver-xorg
and you can put HorizSync	VertRefresh	values according to the spec of your monitor

---

