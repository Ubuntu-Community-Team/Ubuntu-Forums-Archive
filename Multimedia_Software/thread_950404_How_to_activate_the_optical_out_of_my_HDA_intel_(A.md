---
title: "How to activate the optical out of my HDA intel (ALC888)"
date: 2008-10-17
forum: Multimedia Software
---

### Post by fjf on 2008-10-17
I have sound from my HDA intel from the analog out. However, I want to activate the digital (optical) output (which used to work fine before in hardy and lost after a reinstall). aplay -l gives:

aplay -l
**** PLAYBACK list of Hardware Devices****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
Subdevice: 0/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
Subdevice: 1/1
Subdevice #0: subdevice #0

The ALC888 digital is in the System-->preferences-->sound (and gives no sound when selected), but in padevchooser I get only the ALC888 analog to be selected.

Any hints?.

---

### Post by fjf on 2008-10-18
It seems this is a widespread problem:  pulseaudio only recognizes the first device (usually analog) of many sound cards, ignoring the digital out.  There is no fix yet, and this workaround didnt do it for me.  Maybe uninstalling pulseaudio and going back to old alsa would do it?  Any advise?.  Anyone knows how to do it?.  Info:  [http://www.pulseaudio.org/ticket/139](http://www.pulseaudio.org/ticket/139)

---

