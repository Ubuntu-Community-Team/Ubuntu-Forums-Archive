---
title: "sound only through headphones on AC97"
date: 2006-05-21
forum: Multimedia &amp; Video
---

### Post by schacman on 2006-05-21
Hi there,

I'm on a brand new install of Breezy Badger.

Sound card is detected and seems to be working fine.  Volume controls are all up and unmuted.  Problem is that nothing comes out of the speakers.  When I use a headset though, the sound is perfect.

lspci lists my audio card as Intel Corp. 82801BA/BAM AC'97 Audio (rev 12)

I'm a linux newbie so be gentle please.  Thanks!

---

### Post by Fass on 2006-05-21
Type alsamixer in a terminal and choose the proper output there. You might have to unmute it.

---

### Post by schacman on 2006-05-21
Wow, thanks!

Turns out it's a mono output and it was muted by default.  Thanks again!

---

