---
title: "sound from headphone but no sound from speaker"
date: 2011-09-15
forum: Multimedia Software
---

### Post by Khan_77 on 2011-09-15
Hi,
I have a ASUS Eee PC Seashell series, i am running ubuntu 11.04 on it 
but i can't get the sound to work on speakers although i get the sound from headphones at times.The information from alsa shell script is on the following link:-

[http://www.alsa-project.org/db/?f=ab22c5c9a20f19698b6465b39a892534a4af54e0](http://www.alsa-project.org/db/?f=ab22c5c9a20f19698b6465b39a892534a4af54e0)

---

### Post by Toz on 2011-09-22
Try adding:
```
options snd-hda-intel model=auto
```
to the end of **/etc/modprobe.d/alsa-base.conf** and rebooting.

---

