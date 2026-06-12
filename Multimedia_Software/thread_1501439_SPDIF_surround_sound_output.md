---
title: "SPDIF surround sound output"
date: 2010-06-04
forum: Multimedia Software
---

### Post by hamish910 on 2010-06-04
Hi,

Currently using an Asrock ION 330 with an SPDIF output and running 10.04
It works as stereo but can't get the system to run as surround sound and everything shows as 2 channels only.

The hardware itself supports it fine as it works under windows 7 without issues so it has to be a config issue somewhere.

I have tried everything I can find via google including upgrading the alsa drivers but so far there has been no change.

Any suggestions would be great.

---

### Post by hamish910 on 2010-06-06
No ideas hey? :(

If its any help, VT1708S Digital is the SPDIF port

```
htpc@htpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

