---
title: "Geforce 9800 GTX No Sound HDMI"
date: 2012-01-27
forum: Multimedia Software
---

### Post by thinktyler on 2012-01-27
I've done an exhaustive search for a solution. Any links or information regarding how to get HDMI sound to work will be greatly appreciated. 

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
Failed to create secure directory: Permission denied
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
buntu@buntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
Home directory /home/buntu not ours.
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I can't access the sound panel, no devices are listed. I followed some advice, but since I've updated to the latest version of Nvidia's drivers 290.10, I can't do anything.

I've tried using 'alsamixer' but that doesn't enable sound, either.

Alsa version is 1.24.
Ubuntu 11.10

Any help, greatly appreciated.

---

