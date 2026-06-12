---
title: "Display Problems"
date: 2006-07-03
forum: Multimedia &amp; Video
---

### Post by markbworth on 2006-07-03
Under display settings I am only given the screen size options of 640x400@72Hz and 640x480@60Hz. I had had it set at 1024x768@75Hz the other day, but for some reason it changed on me. I checked the driver and I am pretty sure that it is right (sis).

---

### Post by cacharreo on 2006-07-03
Start on terminal mode and run:
***sudo dpkg-reconfigure xserver-xorg***
With this command you'll configure your xserver. Take special care on the monitor section in where you should define the resolutions and frequencies supported by your monitor.;)

---

### Post by markbworth on 2006-07-03
I tried it, but nothing happened. I mean I went through all the questions, but it didn't help.

---

### Post by Starmartyr on 2006-07-03
Read through this thread:

[http://www.ubuntuforums.org/showthread.php?t=208048](http://www.ubuntuforums.org/showthread.php?t=208048)

Hope it helps.

---

### Post by markbworth on 2006-07-03
I ran **sudo dpkg-reconfigure -phigh xserver-xorg** in Konsole and then restarted and it fixed it. I am still not sure what was wrong, but I am happy now. Thanks for the help.

Mark

---

