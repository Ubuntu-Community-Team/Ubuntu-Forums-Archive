---
title: "HELP! Sound card suddenly misidentified"
date: 2010-11-22
forum: Multimedia Software
---

### Post by DatBugler on 2010-11-22
My headphones have stopped working and the only device that now shows up in KDE Settings is "Internal Audio Analog Stereo." In alsamixer, all of the sliders that used to be there appear to be present with the correct settings, including those for the headphone jack, but the card is misidentified as "Intel IbexPeak HDMI," when if I remember correctly it ought to say something like the first entry in the output of aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Help! As far as I know I haven't messed with anything other than volume sliders.

---

### Post by DatBugler on 2010-11-23
Bump.

---

