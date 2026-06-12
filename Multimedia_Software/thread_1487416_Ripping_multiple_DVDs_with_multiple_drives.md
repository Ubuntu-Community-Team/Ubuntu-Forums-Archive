---
title: "Ripping multiple DVDs with multiple drives"
date: 2010-05-19
forum: Multimedia Software
---

### Post by summersab on 2010-05-19
I REALLY like the integration of Brasero in Nautilus - right click, copy disc, and save image. I'm using it to rip my entire DVD collection to my HTPC. Yes, the discs are encrypted, but I have no intention of distributing the media, reburning the discs, or doing anything other than personal use on a single machine, so this is legal where I live.

The problem I'm having is that while I have three DVD drives on this computer, I can only open one instance of Brasero at a time. Using the write click > Copy Disc method from Nautilus on more than one disc and then starting the processes causes each instance to quit. Opening the full Brasero program more than once causes the current instance to simply come into focus.

I've tried dd from the command line, but it won't do encrypted DVDs. Is there any good way to extract multiple commercial DVDs to exact copy ISO files (that's the key - exact copy; I don't want something that Acid Rip or Handbrake puts out)? Better yet, can I force Brasero to open multiple instances?

Thanks!

---

### Post by mc4man on 2010-05-19
While I think brasero is fairly slow and myself usually prefer other methods (also am not tied to .iso's except for certain s.p. disks) -  you can run as many instances as you want - 

 just use terminals

```
brasero -c /dev/sr0
```
```
brasero -c /dev/sr1
```

ect.

too bad brasero doesn't default to <disc label>.iso


edit:
a quick check of brasero would suggest,  if the disc contains structure protection, testing the iso for playability and navigation.
(your only indication from brasero, other than an outright i/o error, would be a slower than usual read,

---

