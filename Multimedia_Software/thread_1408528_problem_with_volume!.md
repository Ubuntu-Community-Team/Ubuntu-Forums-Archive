---
title: "problem with volume!"
date: 2010-02-16
forum: Multimedia Software
---

### Post by behzadsh on 2010-02-16
hi dudes,

I have problem with my system volume. when I turn down volume to 16% or lower it actually muted. I had this problem before on jaunty and i solved it, but in karmic... :D I forget what should I do.

here is some information:
```

$ cat /proc/asound/card0/codec#* | grep Codec
Codec: SigmaTel STAC9228
Codec: Conexant ID 2c06

```

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

```

system information: Dell vostro 1400 laptop / ubuntu 9.10

---

### Post by behzadsh on 2010-02-17
Why it will mute when it turn down to 16% or lower? :confused:
no one has any idea?

---

