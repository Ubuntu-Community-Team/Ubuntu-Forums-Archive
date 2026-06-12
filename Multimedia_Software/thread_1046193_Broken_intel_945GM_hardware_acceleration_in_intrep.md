---
title: "Broken intel 945GM hardware acceleration in intrepid?"
date: 2009-01-21
forum: Multimedia Software
---

### Post by MatBi on 2009-01-21
I recently upgraded from 8.04 to 8.10. To my dismay, xine now takes 100% CPU and complains about dropped frames when i play an mpeg4 (simple profile) video. Under hardy xine was at 60% CPU, the video was silk smooth. Same xine and xorg configuration. 
Intrepid Xorg's log reads "Intel XvMC decoder disabled" which was not in the old logs; I then enabled XvMC in xorg.conf as the man says, without noticeable difference.
Anyone ideas?
Should i post a bugreport?

---

