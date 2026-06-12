---
title: "soundblaster audigy detected but no sound"
date: 2008-08-13
forum: Multimedia Software
---

### Post by DrIdiot on 2008-08-13
I read some of the other threads, but I'm getting different stuff in alsamixer.  I am using the snd-ca0106 driver

Some outputs:
harrison@desolationrow:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH7 [Intel ICH7], device 0: Intel ICH [Intel ICH7]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH7 [Intel ICH7], device 4: Intel ICH - IEC958 [Intel ICH7 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1



I get, for columns,

IEC958, IEC958 Rear, IEC958 Unknown, Analog Center/LFE, Analog Front, Analog Rear, Analog Side, CAPTURE feedback

Most threads tell me to toggle the "Digital/Analog" switch but I can't see it anywhere.

---

