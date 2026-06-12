---
title: "Low Sound"
date: 2010-03-25
forum: Multimedia Software
---

### Post by m00nshine on 2010-03-25
Motherboard: Asus P5KPL-CM
Audio Chipset: VIA VT1708B

No linux sound drivers on Asus' site. No ubuntu 9.10 drivers on VIA site. Low sound with default drivers. I've edited /etc/modprobe.d/alsa-base.conf with options snd-hda-intel model=3stack, but no luck. I actually had to do a sudo sh then edit it that way with vi because it was read only. Didn't do anything.

What do?

:sad:

---

### Post by m00nshine on 2010-03-25
alsamixer was the answer! But should I remove that line from my configuration file?

---

