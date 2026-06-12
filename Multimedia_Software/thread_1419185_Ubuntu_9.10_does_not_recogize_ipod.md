---
title: "Ubuntu 9.10 does not recogize ipod"
date: 2010-03-01
forum: Multimedia Software
---

### Post by GregoryMA on 2010-03-01
Ubuntu suddenly stopped mounting/recognizing my ipod.  The ipod is a 5th generation.  This is not a problem with banshee or rhythmbox.  Ubuntu itself will not acknowledge that I plug the ipod into the usb port.  The ipod will not even charge.  It just acts like I did not plug it in.  Does anybody know how I could fix this?

Greg

---

### Post by boombox1387 on 2010-03-20
Do other USB devices work?  Are you able to mount/use devices like USB flash drives?  If so, have you tried plugging the iPod into different USB ports?  Depending on how your hardware is set up, some ports might be receiving more power than others; if a port isn't receiving enough power, that might explain why it can't charge the iPod.

When the device is plugged in, what is the output it if you run

```
lsusb
```

from a terminal?  This should list everything that is plugged into a USB port.

---

### Post by GregoryMA on 2010-05-05
No devices work in any port I use.  lsusb brings up nothing.

I eventually gave up on this and just waited out for 10.04.  I switched over and much to my chagrin I had the same problem.  I started a new thread here. [http://ubuntuforums.org/showthread.php?t=1473767](http://ubuntuforums.org/showthread.php?t=1473767) 

It seems that this is not a weird problem in 10.04.  Maybe it has something to do with the depreciation of hal?  I'm not sure.

Greg

---

### Post by boombox1387 on 2010-05-05
> **GregoryMA said:**
> No devices work in any port I use.  lsusb brings up nothing.

I eventually gave up on this and just waited out for 10.04.  I switched over and much to my chagrin I had the same problem.  I started a new thread here. [http://ubuntuforums.org/showthread.php?t=1473767](http://ubuntuforums.org/showthread.php?t=1473767) 

It seems that this is not a weird problem in 10.04.  Maybe it has something to do with the depreciation of hal?  I'm not sure.

Greg

That definitely sucks (and it's definitely outside of my scope of understanding).  I would agree that it sounds HAL-related; hope you find some answers!

---

