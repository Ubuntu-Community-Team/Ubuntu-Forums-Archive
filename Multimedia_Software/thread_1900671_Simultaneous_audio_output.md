---
title: "Simultaneous audio output"
date: 2011-12-26
forum: Multimedia Software
---

### Post by Superdude_123 on 2011-12-26
I've had to rebuild my HTPC due to a hard drive failure with Ubuntu 11.10 from 9.10, and I have the system playing its audio through its SPDIF or the standard stereo jack; however, I'd also like to pipe out all the audio through the standard stereo output and the SPDIF (all the audio is handled through the on board sound card of the mother board). I had done this on my 9.10 system, however, I can't seem to figure it out with my 11.10 build. Is there a config file I could dig out of the old hard drive that could have the secret answer?

Also, here's what aplay -l had to say:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia_1 [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia_1 [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia_1 [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia_1 [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Superdude_123 on 2011-12-27
Bump!

---

### Post by Jaykos on 2011-12-28
I'm having the same problem myself. I'm new to Linux and am learning. I'm running the new Ubuntu 11.10 and I get the same simultaneous audio output through the internal and external speakers. 
here's my Alsa link:
[http://www.alsa-project.org/db/?f=223ee3bb0d1a4a8599db05426acf37d964704123](http://www.alsa-project.org/db/?f=223ee3bb0d1a4a8599db05426acf37d964704123)

Hope we can navigate through this, everyone on these forums are very helpful. 

Cheers

---

### Post by Superdude_123 on 2011-12-29
So I gave up on this, and just got a second sound card. If someone finds a solution to this, drop a line in the forms.

---

### Post by lidex on 2011-12-31
> **Superdude_123 said:**
> So I gave up on this, and just got a second sound card. If someone finds a solution to this, drop a line in the forms.

Sorry to be late to the dance. Pulse audio preferences should handle that:
```
sudo apt-get install paprefs
```
Check the box on the "Simultaneous Output" tab.

---

