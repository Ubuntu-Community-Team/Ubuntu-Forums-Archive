---
title: "(Some) audio programs crash audio output"
date: 2010-09-17
forum: Multimedia Software
---

### Post by MattP220 on 2010-09-17
This is an odd issue I'm having, and I'm sure there's some nitpick detail I'm missing. 

What happens is that any audio playback drops out when I open a sound-editing program like Audacity. This also happens with paulstretch and gnaural (both are niche editing programs). 

Just opening those programs while audio playback is happening instantly kills audio output. I have to close and restart the program in question to get sound back. This makes it more of a headache than a real problem, but I would like to get it sorted.

I'm running up to date Lucid, with the following details:

uname -a
```
Linux computer 2.6.32-25-generic #43-Ubuntu SMP Wed Sep 1 09:46:13 UTC 2010 x86_64 GNU/Linux
```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

cat /proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.21.
```

head -n 1 /proc/asound/card*/codec#*
```
Codec: VIA VT1708S
```

Cheers for any help.

---

