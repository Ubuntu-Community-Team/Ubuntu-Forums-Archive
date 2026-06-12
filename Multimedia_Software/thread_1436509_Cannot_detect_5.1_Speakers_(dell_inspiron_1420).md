---
title: "Cannot detect 5.1 Speakers (dell inspiron 1420)"
date: 2010-03-22
forum: Multimedia Software
---

### Post by suxenexus on 2010-03-22
Hi guys!  For some strange reason, I can't activate my 5.1 surround.  The sound preferences only show the 4.0 option.  When I tried using the ```
speaker-test -Dplug:surround51 -c6 -l1 -twav
``` I can only hear the front and rear speakers. Am currently using 10.04.  This problem bugged be since 9.04.

Here's my hardware btw:
```
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Using ```
options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
``` doesn't work too.  Help!

Tried testing the latest beta... but it still isn't working

---

### Post by suxenexus on 2010-03-24
bump

---

### Post by suxenexus on 2010-04-04
somebody help T_T

---

