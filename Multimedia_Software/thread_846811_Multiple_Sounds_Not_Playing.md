---
title: "Multiple Sounds Not Playing"
date: 2008-07-01
forum: Multimedia Software
---

### Post by soritong on 2008-07-01
I'm having an issue playing multiple sounds. If I have Skype open I cannot play music or listen to any sort of videos in Youtube, but if I start listening to YouTube videos I can't initiate a Skype chat.

I'm using ALSA drivers and I made sure Skype is using ALSA drivers, and I've followed the guide for installing the ALSA-OSS package. Any ideas?

---

### Post by soritong on 2008-07-01
Solved this myself after playing around a bit.

I uninstalled Pulse Audio, and then disabled Software Mixing and I can play (at least) 2 sounds at once, havent tried it with more.

---

