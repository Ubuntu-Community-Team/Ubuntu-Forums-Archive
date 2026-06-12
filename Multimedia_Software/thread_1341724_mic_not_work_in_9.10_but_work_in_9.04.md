---
title: "mic not work in 9.10 but work in 9.04"
date: 2009-11-30
forum: Multimedia Software
---

### Post by jiang_lingbing on 2009-11-30
i tried alsamixer,upgrade alsa and pulseaudio, but the mic  still not works
is it because 9.10 sound system differ from 9.04's?
can i change it to 9.04

---

### Post by VertexPusher on 2009-11-30
What kind of mic is it? USB? Plugged into the main soundcard? If it is USB, does ALSA recognize it? What's the output of "arecord -l"?

---

### Post by jiang_lingbing on 2009-11-30
> **VertexPusher said:**
> What kind of mic is it? USB? Plugged into the main soundcard? If it is USB, does ALSA recognize it? What's the output of "arecord -l"?
it is a mic in my 3.5mm hole of soundcard on my mainboard of my laptop.

arecord -l says:
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by smart ali on 2009-11-30
i have the same problem

what shall i do?

---

