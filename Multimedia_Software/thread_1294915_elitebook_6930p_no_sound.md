---
title: "elitebook 6930p no sound"
date: 2009-10-18
forum: Multimedia Software
---

### Post by bradpee on 2009-10-18
ok so im a ubuntu noob and i recently installed ubuntu 9.04 on my elite book and there is no sound. the headphones work but the interneal speakers dont.

i have found that i need to add the line “options snd-hda-intel model=laptop” to /etc/modprobe.d/alsa-base.conf  and thats suppose to take care of it. but i cant figure out how to do it, i tried going into the file but i couldnt save it and i tried stuff in the terminal but no luck.

so could anyone tell me how to do this or if this is even the correct fix?

---

### Post by bradpee on 2009-10-18
nevermind i figured out how to log in as "root" and changed it

---

