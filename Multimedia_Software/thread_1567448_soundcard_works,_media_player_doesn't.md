---
title: "soundcard works, media player doesn't"
date: 2010-09-03
forum: Multimedia Software
---

### Post by Shaheen_rage on 2010-09-03
First time poster here, I'll try and explain my problem as well as possible.

I've installed Ubuntu on my laptop with Ubuntu Studio and my sound card is working correctly (System>preferences>Multimedia Systems Selector, and chose ALSA for the Plugin and my device is the default). The test works, and background system noises work (logging in and out of IM client, etc.) 
But no media player will work, and no sounds from websites work either.

Pretty urgent too, I've gotta record some stuff for my band in a week >.<

any ideas? thanks in advance!

---

### Post by cchhrriiss121212 on 2010-09-04
Is your soundcard onboard or is it an external USB device?
Could you also paste aplay -l into a terminal window and press enter?

---

### Post by Shaheen_rage on 2010-09-04
I've got both, but I'm using my onboard.

when I wrote aplay -l, I got this back:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by lidex on 2010-09-05
You're using jack? Have a look here:
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012](http://ohioloco.ubuntuforums.org/showthread.php?t=843012)
Scroll down to this section - 'Ubuntu Studio and Jack'

---

