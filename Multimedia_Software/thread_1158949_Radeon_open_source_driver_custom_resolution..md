---
title: "Radeon open source driver custom resolution."
date: 2009-05-14
forum: Multimedia Software
---

### Post by paechan on 2009-05-14
Hello fellow ubuntu geeks.

I have recently upgraded my laptop to jaunty and everything went absolutely fine and it is awesome. I then wanted to upgrade my media pc in the living room aswell, but it is a lot older and it is hooked up to a LCD TV, and not a monitor.

Important specs are:

Athlon XP 2200+
Radeon 9600
Ubuntu 9.04 Jaunty fresh install
TV resolution must be 720p or lower, meaning 1280x768 is native and anything above that will cause it to display an error.

When I install Jaunty, I must do it in the safe graphics mode because of this. This all works fine and the driver is set to "vesa" when the system is installed and rebooted.

I then change it to "ati" and reboot. The TV will then be "out of range" meaning the resolution is too high for it. The system works, because I hooked up my old crt monitor to it and I had ubuntu running with compiz and everything.

So basically what I'm asking now is, how do I force the system to start up with a specific resolution? I know the xorg.conf has kinda lost it's power in the newer versions of Ubuntu, but there must still be some way, right?

Any help is much appreciated.

---

### Post by paechan on 2009-05-14
I have also tried with both crt and TV plugged in at the same time, and that way I could set the resolution to something lower and get the TV to display a picture. Only on its own is it a problem.

I really think it's only a matter of forcing the right resolution in xorg.conf

---

### Post by paechan on 2009-05-14
bump  :(

---

### Post by Megamanic on 2009-05-15
Two things.

Old ATI + new Ubuntu means you can't use proprierary drivers.  May not be an issue for a media PC but on the other hand it may be.

Secondly I have found [this]("http://wiki.cchtml.com/index.php/Main_Page") page to be helpful with respect to using ATI cards with Linux.

Not exactly what you want but my xorg.conf skills are minimal

---

### Post by paechan on 2009-05-15
Yes, I know that ATI/AMD stopped support in their newer drivers for the old video cards, but the open source radeon driver works just great when I plug in both monitors. I just need a way of forcing the right resolution.

---

### Post by paechan on 2009-05-15
Hurray!

I think I managed to fix my problem. By editing xorg.conf and adding the modeline part to the Monitor section, I can now chose the right resolution and it looks like its working.

```
Section "Monitor"
	Identifier	"Configured Monitor"
	Modeline "1280x768_60"  80.14  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync

EndSection
```

It's kind of a hack solution, I know, but it works.

---

