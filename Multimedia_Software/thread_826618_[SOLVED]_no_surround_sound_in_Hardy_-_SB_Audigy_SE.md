---
title: "[SOLVED] no surround sound in Hardy - SB Audigy SE (CA0106)"
date: 2008-06-12
forum: Multimedia Software
---

### Post by xjgnsdof on 2008-06-12
I have a 5.1 speaker system hooked up to the Audgy. I don't get sound in the rear left and rear right speakers when I play DVDs in Totem. When I play DVDs in VLC, I don't get sound in the front left and front right speakers.

In Gutsy, I had surround sound just fine by creating an .asoundrc file and setting the channels. I know that there's a problem with the settings for my sound card. Any ideas?

---

### Post by xjgnsdof on 2008-06-12
up

---

### Post by xjgnsdof on 2008-06-14
Solved.

1) create a file in your home folder called .asoundrc
2) copy and paste the following into the file

```
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate}
```

I have done this before, but I removed the file, restarted, and recreated the file after a recent system update.

---

### Post by CLEARviewF on 2008-07-24
This one does not work in Kubuntu KDE4.1 RC1.
Maybe because of Phonon.
Still looking for solutions.

---

### Post by chrisinspace on 2009-12-19
Still works in 9.10 if you have alsa-only apps.  I used it to fix the sound output from MythTv.

---

### Post by adjman on 2011-06-18
Worked a treat, now have surround sound working properly in MythBuntu 11.04

---

