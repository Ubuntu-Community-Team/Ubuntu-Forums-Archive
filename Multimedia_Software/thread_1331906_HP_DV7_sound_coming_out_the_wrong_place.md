---
title: "HP DV7 sound coming out the wrong place"
date: 2009-11-19
forum: Multimedia Software
---

### Post by Brapapple on 2009-11-19
Hey i have a hp dv7-2110sa laptop and have had ubuntu installed for about 3 hours im dualing with windows 7 but neways the problem:

I can only hear sound out of my subwoofer as if it was the primary speaker. i have attempted many quick fixes i have have found myself but am completely lost please please help me i really like ubuntu but this is killing it for me. cheers for your help in advanced.

---

### Post by Brapapple on 2009-11-20
Bamb

---

### Post by darkksyde on 2009-11-20
Go into the terminal and type in alsamixer, try playing around with the controls there and see if that makes a difference.

---

### Post by pi4r0n on 2009-11-26
Do the following

> sudo nano /etc/modprobe.d/alsa-base.conf

and on the bottom of this file add below lines.

> options snd-hda-intel enable_msi=1
options snd-hda-intel model=hp-dv5

reboot system and job done.

---

