---
title: "ALC889a sound problem"
date: 2008-07-18
forum: Multimedia Software
---

### Post by Bonez56 on 2008-07-18
Hi,

I built a new PC today with a Gigabyte M750SLI-DS4 mainboard.
It has a built in Realtek ALC889A sound chip.

I am running Hardy x86. All sound, including system sounds, streaming radio, youtube etc is extremely jittery and crackly.

I use a Logitec 5.1 sound system that is connected by the analog ports (black, yellow, green 3.5mm plugs).

I have tried everything I can think of, google returns nothing and nobody else seems to report this issue.

Please help! 

```

blake@horizon:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

blake@horizon:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC885

```

Is the wrong module being loaded, or is there no support for my 889 chip? How can I load the 889 module?

Thank you!:confused:

---

