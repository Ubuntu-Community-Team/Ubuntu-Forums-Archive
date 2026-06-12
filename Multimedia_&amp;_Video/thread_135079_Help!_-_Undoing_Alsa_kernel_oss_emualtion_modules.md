---
title: "Help! - Undoing Alsa kernel oss emualtion modules"
date: 2006-02-23
forum: Multimedia &amp; Video
---

### Post by speedsix on 2006-02-23
Hi, 

Somewhere along the line I seem to have got my system to load the also oss emulation modules *snd-pcm-oss* etc. as they show up in lsmod | grep "oss".

I don't want to use kernel emulation I want to use *aoss* so I can use software mixing, problem is I'm not sure how to stop the snd-pcm-oss and other alsaoss modules loading at startup?

There's nothing in /etc/modules but there are references in /etc/modutils/alsa-base

I have tried commenting these out, can't remember what I added to get the modules to load on startup in the first place. No joy though they still show up with lsmod on every boot.

Or do I just leave these modules?

Any ideas?

Many thanks

---

