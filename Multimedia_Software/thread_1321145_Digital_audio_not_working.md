---
title: "Digital audio not working"
date: 2009-11-09
forum: Multimedia Software
---

### Post by plueken on 2009-11-09
I am trying to get my optical digital output working so that I can hook my PC up to my sound system.  This works in Vista, and I was able to get it to work in 9.04 by activating the IEC958 checkboxes in alsamixer, but I haven't found a way to get anything other than analog working in 9.10 with PulseAudio.

My aplay -l says
```
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

My aplay -L says
```
front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
```

In the Sound Preferences dialog, I am able to see Digital Stereo Duplex (IEC958) and Digital Stereo (IEC958) Output + Analog Stereo Input, but selecting either of those just causes there to be no sound output at all.

Any help is greatly appreciated!  Thanks!

---

