---
title: "Blue Hue in all Video"
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by tmada on 2008-01-26
Last night I was messing around installing media players and codecs and one of them caused this problem where every video played (no matter which player) would have a blue hue over it.

Does anyone know what this could have been caused by or is there possibly a log I can check to see what I installed last night?

Thanks

---

### Post by fedex1993 on 2008-01-26
are you using the default movie player on videos because if you are it sucks badly. I recommend isntalling mplayer(sudo apt-get install mplayer) and also the mozzila plugin(sudo apt-get install mozilla-mplayer) and then if there still is a blue hue post back and i can help again

---

### Post by tmada on 2008-01-26
I am currently using mplayer. 
This is what I did to fix this issue:


I went into mplayers preferences and moved the hue bar to 0 (all the way to the left). This made videos appear to be normal.

---

### Post by kerry_s on 2008-01-26
in the settings change the video output to "open gl", i get the same thing in vlc.
settings pic->

---

### Post by tmada on 2008-01-26
switching to opengl worked great.
Thanks

---

### Post by multisimple on 2008-06-25
[http://ubuntuforums.org/showthread.php?t=484515](http://ubuntuforums.org/showthread.php?t=484515)

---

