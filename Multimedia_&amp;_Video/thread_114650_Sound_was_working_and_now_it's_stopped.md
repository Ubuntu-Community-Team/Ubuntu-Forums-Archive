---
title: "Sound was working and now it's stopped"
date: 2006-01-09
forum: Multimedia &amp; Video
---

### Post by CujoQuarrel on 2006-01-09
Title says it all. The sound was working fine and now nuttin..

Dual boot system and hdw is working on the PC side still.

Any suggestions on how to diagnose. I figure I've hit a setting somewhere but  I can't find it. Looked at all of the sound GUI's that I can find.

CujoQuarrel

---

### Post by eriksundelof on 2006-01-09
Try running *alsaconf* (if you do not have it you need to install ALSA either by packages or compile directly from [http://www.alsaproject.org](http://www.alsaproject.org))

Remember to load in the module (most often sound is run through modules these days) by *modprobe snd-"cardname"*...

---

### Post by CujoQuarrel on 2006-01-09
No alsaconf on the system. Where would I find a package for it. The site you listed [www.alsaproject.org](www.alsaproject.org) may have it but can't find anything but ads there.

---

### Post by eriksundelof on 2006-01-09
Sorry the link should be [http://www.alsa-project.org/](http://www.alsa-project.org/)

---

