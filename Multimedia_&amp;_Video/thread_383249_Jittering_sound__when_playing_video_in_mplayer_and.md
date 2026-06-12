---
title: "Jittering sound  when playing video in mplayer and alsa , but normal with esd"
date: 2007-03-13
forum: Multimedia &amp; Video
---

### Post by uboltun on 2007-03-13
So the title says it all.  When I run mplayer with option -ao alsa I have sound breaks every few seconds. If I play same file but -ao esd everything works fine. Interestingly, sound breaks are always at a certain position. I have encountered this behavior only for a few video files and sometimes with DVDs. Any ideas on why is this happening ?

---

### Post by uboltun on 2007-03-19
I found the solution here: 
[http://ubuntuforums.org/showthread.php?t=301491&highlight=alsa+slow](http://ubuntuforums.org/showthread.php?t=301491&highlight=alsa+slow)
Changing from ALSA to OSS fixed the sound problem. Still can't figure out what is the difference between the two of them ...

---

