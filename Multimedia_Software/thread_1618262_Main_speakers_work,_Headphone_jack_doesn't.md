---
title: "Main speakers work, Headphone jack doesn't"
date: 2010-11-10
forum: Multimedia Software
---

### Post by Pntbllfrk on 2010-11-10
Hello,

The problem I'm having is that when I plug in my headphones into my asus g60vx laptop I do not have sound, however if I unplug them I have sound through my laptop speakers.


[http://www.alsa-project.org/db/?f=5f531963e4166693437f0bdaa1dcf5630e12d00e](http://www.alsa-project.org/db/?f=5f531963e4166693437f0bdaa1dcf5630e12d00e)

Ubuntu 10.10

Thank you!

---

### Post by Pntbllfrk on 2010-11-11
Fixed, thanks to lidex on another topic,

```

1.gksudo gedit /etc/modprobe.d/alsa-base.conf
2.add options snd-hda-intel model=auto at the end of the file

```

---

