---
title: "No sound, out of ideas"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by Geezle on 2008-01-31
Hey folks, I've been seeing a lot of similar threads here, but I have to start another one.  I've lost all sound on my Gutsy install and I can't figure out what's up.  I've read through as many of the other posts concerning this problem, including the Comprehensive Sound Problem thread and I can't figure out what's up.  

I noticed a couple days ago that my machine suddenly had no sound.  I came on here and tried pretty much everything there was concerning this issue, but nothing seemed to work, so I decided to try a new install, but I'm still having the same problem.  I've also tried rebuilding alsa with no success.

A lot of the issues I've read about seem to concern Intel modules, but is not my case.

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
It sees my sound card and all my audio controls seem to be intact so I'm not sure what to do.

I have tried installing the linux-backports-modules package, rebuilding ALSA, and a few other things I can't remember anymore, but with no luck.  

Any help would be greatly appreciated.

---

