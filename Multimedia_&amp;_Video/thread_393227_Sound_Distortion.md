---
title: "Sound Distortion"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by richbiskit on 2007-03-25
Just upgraded from edgy to feisty, everything works fine but i get poor sound quality from any media player like amrok or rhythmbox. The base is ok but the trebble is horrible :(  Using either intel ich6 (alsa mixer) or conexant id 30 (oss mixer) on tosh sat pro l20. 

Had no problems in windows, ubuntu or kubuntu :(

---

### Post by .oops on 2007-03-26
I have the same problem using Xfmedia. I'm using the ALSA driver. Any ideas? :(

**Nevermind**, fixed it. Just lowered some values in alsamixer, all of them to about 75, and then raised the speakers volume itself. No more sound distortion. :)

---

### Post by richbiskit on 2007-03-28
worked for me too :guitar: thanks for posting the tip!

---

### Post by speedman on 2007-03-30
I found the setting for "Master Mono" was maxed by default on my install of Feisty.  Sound was distorted and muting didn't work until I set the "Master Mono" level to it's lowest level.

HTH

SM

---

### Post by penvzila on 2007-04-28
Wow, do I feel stupid.  This fixed my last remaining issue with my sound card.  Thanks!

---

