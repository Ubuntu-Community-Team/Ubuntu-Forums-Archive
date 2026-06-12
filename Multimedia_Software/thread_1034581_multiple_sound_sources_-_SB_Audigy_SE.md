---
title: "multiple sound sources - SB Audigy SE"
date: 2009-01-08
forum: Multimedia Software
---

### Post by xjgnsdof on 2009-01-08
I use CA0106 as my sound driver. I set everything to ALSA in my Sound properties. How do I enable Ubuntu to play multiple sound sources?

---

### Post by xjgnsdof on 2009-01-09
up

---

### Post by markbuntu on 2009-01-09
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by xjgnsdof on 2009-01-10
Those are all general fixes to get sound to work. I hear sound; I just only hear it in one program at a time. I need a fix for the SB Audigy SE that lets me hear multiple sound sources.

---

### Post by markbuntu on 2009-01-10
Did you follow the directions in the link?
If you did you are able to do that.

---

### Post by xjgnsdof on 2009-01-11
I don't want to switch to Pulse Audio. I just want multiple sound sources in ALSA.

I have the following .asoundrc, which apparently only allows stereo to play through all five of my speakers, but does not allow multiple sound sources:

```
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate}
```

How do I keep my stereo surround AND have multiple sound sources?

---

### Post by xjgnsdof on 2009-01-12
up

---

### Post by markbuntu on 2009-01-12
> **elgilicious said:**
> I don't want to switch to Pulse Audio. I just want multiple sound sources in ALSA.
....

How do I keep my stereo surround AND have multiple sound sources?

Well good luck with that. I looked and looked and looked for ways to do that with alsa and without pulseaudio and never did find an answer.

---

