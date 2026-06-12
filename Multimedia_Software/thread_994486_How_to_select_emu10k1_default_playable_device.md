---
title: "How to select emu10k1 default playable device?"
date: 2008-11-26
forum: Multimedia Software
---

### Post by gyurman on 2008-11-26
Hy,

I have a ~/.asoundrc file.
```
pcm.emu10k1 {
          type hw
          card Live
           }
       
       ctl.emu10k1 {
          type hw
          card Live
       }
```
I play a stereo sound:
alsaplay -d emu10k1 stereo.mp3
I hear music in 5.1.

But I play this method:
alsaplay -d emu10k1 stereo.mp3
I hear music only on front.
Why?

How can i set the emu10k1 should be default?

---

