---
title: "Another sound problem ubuntu 7.04 ALSA"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by nico-ar on 2007-06-29
hello i have a problem with the sound.. i cant play sond for alsa..
i used ubuntu 6.04 and this work perfect but i do the upgrade to 7.04 and now dot work
here a error [IMG]http://img217.imageshack.us/img217/715/screenshot1jm0.png[/IMG]

i reinstalled alsa 1.0.14 but this dont work :(
help me

---

### Post by dkd903 on 2007-06-29
terminal>gksudo gedit /etc/modprobe.d/alsa-base

Add the following line to the end of the file, replacing '3stack' with your flavor and the brand wid ur card`s manufacturer (see below) :

options snd-hda-brand model=3stack

---

### Post by nico-ar on 2007-06-29
i add this: options snd-hda-nvidia model=ck804
its ok?

---

