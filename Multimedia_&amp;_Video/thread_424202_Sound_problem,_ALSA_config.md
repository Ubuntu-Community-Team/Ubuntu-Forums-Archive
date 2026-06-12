---
title: "Sound problem, ALSA config?"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by Patrick K on 2007-04-26
Since upgrading to Feisty, I have a sound problem with Audacity. Recordings skip and make noise during playback. The same recordings do not do this in Windows. 

I took a look at "/usr/src/alsa/alsa-driver-1.0.13/config.log" file and found it says > uname -r = 2.6.17-10-generic This is the wrong kernel (should be 2.6.20-15-generic). 

I'm not sure how to correct this. Should I try attempt recompiling the existing drivers (I don't know if this is possible) or download again (the version is the same), delete the existing files (a good chance I won't find them all) and compile from scratch?

---

### Post by Patrick K on 2007-04-27
Bump

---

### Post by Patrick K on 2007-04-29
bump

---

### Post by Patrick K on 2007-05-02
bump

---

### Post by rockingmtranch on 2007-05-02
Have you tried removing and replacing the alsa package from this how to?
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Just a thought.

---

