---
title: "Sabrent SBT-TVFM (saa7130) - Ubuntu Hardy How-to"
date: 2008-06-29
forum: Multimedia Software
---

### Post by abray on 2008-06-29
For anyone using the Sabrent SBT-TVFM TV Tuner card with Ubuntu Hardy, I just figured out the Modprobe options line that seems to work great with Xawtv and TVTime!  Copy the following into /etc/modprobe.d/alsa-base

options saa7134 card=42 tuner=43

I am able to see all channels (73+) and sound is perfect.  Good luck!

---

