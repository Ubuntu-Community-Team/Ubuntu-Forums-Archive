---
title: "Using two headphones simultaneously on hp dv3"
date: 2010-01-13
forum: Multimedia Software
---

### Post by tjodSK on 2010-01-13
Hello!

i've got an HP dv3550 notebook with two headphone jacks in the front (both works simultaneously in windows). Sound works, if i plug headphones in either jack the internal speakers are switched off. Both jacks produce sound, but, only one at a time. If i plug headphones in the right jack, internal speakers are muted and i can hear sound through the headphones. However, if i put another headphones in the left jack, the first headphones are muted.

I would like to use them simultaneously. Is there any fix available?:
```

lshw | grep Audio
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller

```


```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

aplay --version
aplay: version 1.0.21 by Jaroslav Kysela <perex@perex.cz>
uname -a
 2.6.32.3-core2 #1 SMP Thu Jan 7 22:17:11 CET 2010 x86_64 GNU/Linux

```

---

