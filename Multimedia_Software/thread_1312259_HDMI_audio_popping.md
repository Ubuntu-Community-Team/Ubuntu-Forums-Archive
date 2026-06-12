---
title: "HDMI audio popping"
date: 2009-11-03
forum: Multimedia Software
---

### Post by u-slayer on 2009-11-03
I have a motherboard with ati graphics and integrated HDMI audio. Whenever I tried to play it, it makes a horrendous popping sound.


I found the fix on youtube, so I want to share:

Open a terminal and type:
gksu gedit /etc/modprobe.d/alsa-base.conf

Then just comment out that last line (#options snd-hda-intel power_save=10) and save and restart.

---

