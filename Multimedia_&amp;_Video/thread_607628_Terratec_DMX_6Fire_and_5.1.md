---
title: "Terratec DMX 6Fire and 5.1"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by cisoprogressivo on 2007-11-09
Hi
I have a Terratec DMX 6 Fire soundcard with a 5.1 system.
I use this .asoundrc to get all the speakers working:
```
pcm.!default {
 type asym
 playback.pcm {
 type plug
 slave.pcm {
 @func concat
 strings [ "dmix:0,FORMAT=S32_LE" ] #card number 0
 }
 ttable.0.0 1
 ttable.1.1 1
 ttable.0.2 1
 ttable.1.3 1
 ttable.0.4 0.5
 ttable.1.4 0.5 
 ttable.0.5 0.5 
 ttable.1.5 0.5
 }
 capture.pcm {
 type plug
 slave.pcm {
 @func concat
 strings [ "dsnoop:0,FORMAT=S32_LE" ]#card number 0
 }
 }
 }
```

but the sound is not splitted, and i hear hight and bass sound from all the speakers.
Can someone help me?
Thank you

Emanuele

---

