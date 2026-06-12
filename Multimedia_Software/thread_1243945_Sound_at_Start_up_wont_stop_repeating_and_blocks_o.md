---
title: "Sound at Start up wont stop repeating and blocks out other sounds"
date: 2009-08-18
forum: Multimedia Software
---

### Post by StandTogetherNow on 2009-08-18
So I&#7743; having a problem with my sound. At start up, this bump sound starts and won stop. It keeps repeating and repeating and repeating. Because of this I can´t hear sound on anything else. It reads sound files alright, I just can´t hear them at all. I use an HP Pavilion dv7 with an HDA Intel card and STAC92xx analog and digital device. I run Ubuntu 9.04

Any help?

---

### Post by kiserp on 2009-08-19
Oh, I have a same problem with my laptop Asus A6R (chipset ATI IXP SB400).
 but on start all is OK and sound pass to cycle  when I start my player.

---

### Post by mparlaktuna on 2009-08-21
Hi,
I had the same problem with HP dv7 laptop. Adding

options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

these lines at the end of the file 

/etc/modprobe.d/alsa-base.conf

worked for me. After adding do not forget to restart your computer.

---

