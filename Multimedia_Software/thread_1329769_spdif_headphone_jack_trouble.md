---
title: "s/pdif headphone jack trouble"
date: 2009-11-17
forum: Multimedia Software
---

### Post by moeshroom on 2009-11-17
i have had this trouble in intrepid (clean install), jaunty (clean install), and karmic (package manager upgrade) ever since i got this computer in march.  the machine is an asus n80vn notebook.

the headphone jack (analog) works properly in windows but not in ubuntu.  the funny thing is if i unseat the plug by just a hair, i do get stereo output but with a slight buzz.  i have tried all the different combinations in "sound preferences."

the internal speakers do work properly in ubuntu as does a generic chinese usb stick card.

i should mention that in order to get my sound to work at all i had to add the following line to the /etc/modprobe.d/alsa-base file:
```
options snd-hda-intel enable=1 model=g50v position_fix=0
```


```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

thanks folks.

---

### Post by moeshroom on 2010-01-08
bump

---

