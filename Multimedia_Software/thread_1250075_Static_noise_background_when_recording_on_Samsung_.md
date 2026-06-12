---
title: "Static noise background when recording on Samsung NC10 / sound device ALC272"
date: 2009-08-26
forum: Multimedia Software
---

### Post by jbaach on 2009-08-26
Hi *,

I am trying to setup an Samsung NC10, with voip / skype being one of the main use cases. I use 9.04 so far (but also tested
9.10 and 8.10)

Sound playback works fine so far. The problem is recording - even though the laptop clearly records my voice (internal and external) no matter what I do there is always a background static noise, that increases and decreases with the overall volume of the recording. 

I tried this with the audio recorder as well as skype. I have this behaviour no matter what device I set in 'audio' for recording.

When testing with WindowsXP everything works fine - so its not an hardware issue.

lspci:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

aplay -l:
Karte 0: Intel [HDA Intel], Gerät 0: ALC272 Analog [ALC272 Analog]

Any ideas?

Cheers,

  Joerg

---

