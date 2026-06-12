---
title: "No sound in Ubuntu 8.10"
date: 2009-04-15
forum: Multimedia Software
---

### Post by truthypants on 2009-04-15
Hi there,

I recently installed Ubuntu 8.10 (32-bit) on a second internal HD. Everything went well and it installed almost without a hitch, but I later discovered that I get no sound.

I have read through the "Comprehensive Sound Problem Solutions Guide" and tried everything on there, but nothing seems to work. I've also searched through this forum and on Google but none of the solutions from there work either. 

I've also checked my alsamixer to ensure that none of the channels are muted and I tried the fix whereby you get rid of pulseaudio, but that didn't work.

I also have the correct permissions. 

Here are the details of my soundcard:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I appreciate any help that you can offer me. I am totally new to this so apologies if I'm being stupid.

---

### Post by daboroe on 2009-04-15
What are the output sound devices set to? HDA or like ALSA, etc?

---

### Post by truthypants on 2009-04-15
Here are my Sound Preferences - there may be some discrepancies here but I have tested every output method and none work.

[IMG]http://img167.imageshack.us/img167/5444/soundprefs.png[/IMG]

---

### Post by markbuntu on 2009-04-15
Extensive troublehsooting help is here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

