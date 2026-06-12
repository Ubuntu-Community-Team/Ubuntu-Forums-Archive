---
title: "ALSA trouble"
date: 2011-09-30
forum: Multimedia Software
---

### Post by katie74656 on 2011-09-30
Hi everyone!

I've just upgraded to Ubuntu 11.4 and i have trouble with getting the sound to work. I managed to get sound with gnome-alsamixer and then un-muting "Analog C" and "Analog R", but then Linux crashed and I couldn't get it to work again, i.e. I un-muted "Analog .." again but it didn't work. 

My Alsa Info File: [http://www.alsa-project.org/db/?f=ad2ce3dc9bad72902370bbe1d69de7bb49861719](http://www.alsa-project.org/db/?f=ad2ce3dc9bad72902370bbe1d69de7bb49861719)


[COLOR=Sienna]**EDIT: Already solved: In the gnome-alsamixer: "IEC958" must not be checked**[/COLOR]

---

### Post by anieruddha on 2011-09-30
Try downloding latest alsa driver from [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page). And install it

Installing instruction u can find in archive. Also u can refer 
[http://alsa.opensrc.org/Quick_Install](http://alsa.opensrc.org/Quick_Install).

Also first check your sound card support here : 
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

---

### Post by mörgæs on 2011-09-30
Good, please mark the thread 'solved' using 'thread tools'.

---

