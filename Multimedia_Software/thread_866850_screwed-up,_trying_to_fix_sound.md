---
title: "screwed-up, trying to fix sound"
date: 2008-07-22
forum: Multimedia Software
---

### Post by Trollax on 2008-07-22
Okay. So I just installed hardy on my acer aspire 5720G. Having the same old 'jack sense' issue that previous versions had (i.e. when you plug headphones in the laptop speakers still play). Only this time it doesn't look like there's a simple check-box to enable it.

Silly me tried to fix it with [_this_](http://ubuntuforums.org/archive/index.php/t-765867.html) Only the second step failed partway through, and now I have *zero* sound.

when I type in:
```

aplay -l

```

I get:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

No sound devices are muted. Is there any way I can undo what I did?

---

