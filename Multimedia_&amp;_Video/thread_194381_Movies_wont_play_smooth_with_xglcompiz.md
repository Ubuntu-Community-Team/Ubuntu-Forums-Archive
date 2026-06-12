---
title: "Movies wont play smooth with xgl/compiz"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by pratzabrat on 2006-06-11
i have posted this in two other threads, but to no avail. I am running Ubuntu 6.06 on an AMD64 2800+ w/ Nvidia 4000 MX graphics card. Once I install xgl/compiz for the eyecandy thing (following ubunut wiki) and make the changes in the conf files, my movies dont play well in the fullscreen mode. But as soon as I reverted the xconf n the gdm files to the backed up ones, the thing is fine. Now I love the sweet window functions which come along with xgl/compiz and also am a movie buff. Please dont ask me to choose one. Thanks.

---

### Post by XAsmodeanX on 2006-06-11
Choose one.  XGL/compiz is still under heavy development and it does admittedly have issues with movies playing but the best combo I've found is to use mplayer and use either the xv or gl2 plugin.  They seem to offer the smoothest playback.

---

### Post by pratzabrat on 2006-06-11
The inconsistencies dont stop with movies. Even the planetpenguin racer aka tuxracer (yeah i m a li'l boy) dont run fine. So is it really true that xgl/compiz is unstable.

---

### Post by Patrick-Ruff on 2006-06-11
I suppose so, it'll get better as developement goes on. but for the time being its a little above alpha stage. we'll see tho, what video card are you running on? what are your system specs? such things could have an effect on an extremely 3d graphic system.

---

### Post by pratzabrat on 2006-06-11
My hardware specs :
AMD 2800+ 64 bit
Nvidia 4000 MX (128 MB)
512 MB RAM
K8TM MSI motherboard

---

### Post by whatever on 2006-06-11
[QUOTE=pratzabrat]Nvidia 4000 MX (128 MB)[/QUOTE]
no pixelshader support -> no xv emulation via fbo in xgl -> slow video performance

you should stay with plain xorg :)

---

