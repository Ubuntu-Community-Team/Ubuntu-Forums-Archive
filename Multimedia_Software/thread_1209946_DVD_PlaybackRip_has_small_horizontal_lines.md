---
title: "DVD Playback/Rip has small horizontal lines"
date: 2009-07-10
forum: Multimedia Software
---

### Post by TwiceOver on 2009-07-10
Never really cared about playback so much as being able to rip my discs over to my HTPC.  Anyway, on my main machine watching a DVD in any program has small horizontal lines through quick action sequences.

The odd part of this is that it also translates through to a dvd rip.

The system is a Dell Inspiron 530, Celeron 2ghz, 2gb ram, Onboard Intel video.

I'm not sure what could cause this, it is very annoying however.  I don't have any other Ubuntu systems that I can try this on currently.

Hrm...

Ubuntu 9.04 for reference.

EDIT:  Installed a PCI-E Nvidia card with 256mb ram (the onboard could only use 8mb) in hopes of better quality... No go.

---

### Post by TwiceOver on 2009-07-11
Bump

---

### Post by mc4man on 2009-07-11
If the orig. source material is interlaced then you may be seeing interlace artifacts. Try using a deinterlacer, every player has at least one. (method

Or you may be seeing a slight horizontal tearing, if so you can try a number of things or combo of things

Enable or disable  vsync in compiz and nvidia settings
Enable  or disable 'Unredirect fullscreen Windows' in compiz
Turn off compiz 
Try a different nvidia driver
Go back to 8.04

---

### Post by neveruse513 on 2009-07-29
same here.

just built one with an i7 920, geforce 260 216, 6gb corsair, yada yada... 9.04.

horizontal lines during full screen playback (or just big enough) of pretty much any fast moving portions of video. dvd fresh out of the plastic wrap, tv tuning, flash... i've got two burners (both new, one nice) and it happens on both.

it can usually be reproduced at the exact same point in the movie, but not always. it's usually at the same position on the screen, too, but not always. so i'm doubting it's the dvd.

compiz is already off, maybe i'll turn it back on and play with some of the options. or try some older (or beta?) nvidia drivers. if it comes down to it, roll back through the releases until i get it right.

if anyone else out there is having this problem with a card other than an nvidia, please let me know.

suggestions welcome. otherwise, stay toond.

---

