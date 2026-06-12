---
title: "Media playback (audio or video) glitches lately"
date: 2012-07-10
forum: Multimedia Software
---

### Post by mjpatey on 2012-07-10
Hi, all-

Running Ubuntu 12.04 64-bit on a quad-core i5 Sony VAIO laptop. Not new to Ubuntu, but I have to say I haven't needed to poke around at its internals in quite some time. A good sign for the OS, but as a result, I'm a bit rusty!

Started having problems recently playing Flash videos in Chrome and Firefox, and have noticed it happens when playing other Flash media, as well (like auditioning a song on a website). And today I just discovered it happens when playing audio or video in Rhythmbox. Sometimes the media will "freeze" on a 1/4-second chunk and repeat it a few times before continuing (a la Max Headroom), and sometimes it just plays through the whole thing at super-fast speed. This happens both with video and audio-only playback.

Any idea where I can go to fix something this pervasive (covering audio, video, Flash content in both Firefox and Chrome, as well as Rhythmbox playback)?

Thanks for any light you can shed!

-Mark

---

### Post by mjpatey on 2012-07-12
This doesn't appear to be a problem with Flash, as it happens with just about every type of audio/video media... so I suspect something higher up the chain. A gstreamer or ffmpeg problem, or something along those lines, maybe?

Any insight from someone who knows this stuff better than I do would be greatly welcomed!

-Mark

---

### Post by Soynct on 2012-07-13
This really answered my problem, thank you!

---

### Post by wargoth on 2012-07-31
Hi! Have you resolved this issue? I have the same problem on my desktop. It started glitching just recently, a month ago or so. It's really annoying! Sound devices:

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have already tried setting sample-rate to certain values, tried load-module module-udev-detect tsched=0 with no success. Any clues?

---

### Post by wargoth on 2012-08-21
Any ideas? Please!

---

