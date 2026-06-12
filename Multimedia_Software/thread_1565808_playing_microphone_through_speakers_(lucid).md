---
title: "playing microphone through speakers (lucid)"
date: 2010-09-01
forum: Multimedia Software
---

### Post by Mirrorboy on 2010-09-01
I'm trying to set something up so I can hear my microphone in real time through my speakers. I've done it on Windows, but I can't find the setting in Ubuntu Lucid. Is there a way to set it up without using other software? I tried using Audacity and it worked, but not the way I wanted it to. I'm talking about setting it up from within the OS like in Windows.

---

### Post by Mirrorboy on 2010-09-02
Bump. Anybody know anything about this?

---

### Post by lidex on 2010-09-03
Try installing paprefs:
```
sudo apt-get install paprefs
```
On the 'Multicast/RTP' tab you'll want to tick the second option and in the sub-options select 'Loop back audio to local speakers'

---

