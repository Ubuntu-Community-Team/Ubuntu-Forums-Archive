---
title: "VLC sound during video cuts out after a while"
date: 2008-05-30
forum: Multimedia Software
---

### Post by robog2 on 2008-05-30
Watching an AVI in VLC (this happens with every AVI I play), the sound works fine for a while, then cuts out (after anywhere from five to twenty minutes), giving me the following errors repeatedly:

> oss error: write failed (Input/output error)

> main debug: audio output is too slow (613567), trashing 21333us

> main warning: audio drift is too big (137288 ), dropping buffer


Sound in the video comes back once I have changed _any_ audio setting in VLC (except for volume), and then cuts-out again later (and comes back after changing the setting again or another setting).  

This problem only arises when watching a video, and to my knowledge only in VLC (totem runs too slow to watch a video anyways).  This problem was not present before I switched from alsa to OSS4.  I am running Hardy, and everything else related to sound works fine.

---

### Post by Amazona aestiva on 2008-05-30
I had had an error like yours, until I compiled the latest from source code. There is the 'e' version in th repo, and the latest is 'f'.

Hope this would help!

Good luck

---

### Post by robog2 on 2008-05-30
Thanks!  I'll try it out.

---

