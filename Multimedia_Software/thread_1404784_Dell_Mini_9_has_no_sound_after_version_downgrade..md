---
title: "Dell Mini 9 has no sound after version downgrade."
date: 2010-02-11
forum: Multimedia Software
---

### Post by Jeconti on 2010-02-11
I got fed up with 9.10 issues, so I downgraded back down to Hardy. Never had a problem before, then after the downgrade, there was no sound.

aplay -l yields the following
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Just for good measure, I added snd-hda-intel to my /etc/modules file.

Doubled checked ALSA mixer, it is not muted and the volume is at full.

I recompiled the ALSA driver to no avail.

Other ideas?

---

