---
title: "Poor Sound Quality After Messing with ZSNES  / libsdl"
date: 2008-04-30
forum: Multimedia Software
---

### Post by shinkaide on 2008-04-30
Hi all, I'm experiencing poor sound quality; namely, crackling sound, especially with the low bass frequencies when playing music through exaile and amarok.

From a fresh Hardy install, everything sounded pristine. But when I installed ZSNES and couldn't get any sound, I followed the [advice in this thread]("http://ubuntuforums.org/showthread.php?t=733387") to get sound to work in ZSNES and that's when sound quality went to hell.

Basically I installed **libsdl1.2debian-all** and I think that may have something to do with it, but I don't know where to go from there. 

I've tried switching devices on the volume preferences, but I don't think those're it...

Help please?

---

### Post by aeiah on 2008-04-30
i dont think its the devices you need to change, but more the oss bit. it seems you perhaps changed your sound from alsa or pulseaudio to oss systemwide. have you tried changing it to alsa or whatever it was before?

---

