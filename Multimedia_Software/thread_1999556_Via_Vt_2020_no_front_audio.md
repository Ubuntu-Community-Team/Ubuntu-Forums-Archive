---
title: "Via Vt 2020 no front audio"
date: 2012-06-08
forum: Multimedia Software
---

### Post by Fulgur on 2012-06-08
Hi guys, 

I hope you can help me with this since I allready spent hours on this issue.
I have an onboard VIA VT2020 sound chip and I can't get the front headphone jack do work. I allready updated to alsa 1.0.25 with an update script ftom this forum. Also I added options snd-hda-intel model=auto do my alsa-base.conf. Ubuntu shuts off the sound from the backside jack when I plug in headphones but I don't get any sound from them.

Can you help me?

Regards
Lukas

---

### Post by Fulgur on 2012-06-08
Would a kernel update change anything?

---

### Post by Fulgur on 2012-06-09
push

---

### Post by rei12 on 2012-06-10
I have the same problem here (using VIA VT2020 from Gigabyte GA-Z77M-D3H). Rear audio jack works fine, but front audio jack doesn't.

Operating System: Ubuntu 12.04 (64 bit)
ALSA Information: [http://www.alsa-project.org/db/?f=52ca9bdd914bab420d64e968ec3094fbb759b447](http://www.alsa-project.org/db/?f=52ca9bdd914bab420d64e968ec3094fbb759b447)

Does anyone have solution for this?

---

### Post by Fulgur on 2012-09-05
It is working now on Fedora 3.5.3-1.fc17.x86_64, might be fixed in Ubuntu, too.

---

