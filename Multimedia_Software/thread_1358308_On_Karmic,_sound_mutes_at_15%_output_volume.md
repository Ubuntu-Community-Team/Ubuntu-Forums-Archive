---
title: "On Karmic, sound mutes at 15% output volume"
date: 2009-12-18
forum: Multimedia Software
---

### Post by gkkg on 2009-12-18
I started getting this since upgrade to Karmic (64bit). When adjusting the sound volume, at 16% volume output the sound works, but when lowered to 15%, it just mutes. I have a Dell Latitude D630 laptop. Any help much appreciated...

---

### Post by russianzilla on 2009-12-22
I have the same problem here on Karmic 32-bit on a Dell XPS 410 desktop. The sound card is a SigmaTel STAC9227. I was playing with the volume while looking at alsamixer and noticed that when the Karmic volume control is set to anything below 16%, the master volume in alsamixer is set to 0 and the PCM and Front volumes are both set to 100. PCM decreases sound normally, while lowering Front at all completely mutes the sound. When everything is set to 0, raising Karmic's master volume to 1% boosts PCM to 64% and PCM/LFE to 99-100% at around 3% master. Any suggestions? From what I can tell, the problem is that Karmic's volume control isn't quite in sync with alsamixer.

---

