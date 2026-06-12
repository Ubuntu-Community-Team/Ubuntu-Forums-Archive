---
title: "Sound problems"
date: 2008-08-07
forum: Multimedia Software
---

### Post by Fen_Star on 2008-08-07
I am having sound problems with my onboard [cm6501]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-C-Media") card on a ASUS m2n-sli board.
I'm not certain the problem is with my sound card, because alsamixer doesn't work. I have no sound at all.

I have tried the comprehensive sound solutions guide but gotten nowhere.
I have reinstalled alsa, etc.

There seem to be other people who have had problems with this chip, but none of them said alsamixer didn't work. I have also seen things that say this chip works with alsa.

I would love to get sound over HDMI, :P But I don't ever expect that to happen. any help would be appreciated. 

```
 alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
```

```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
 lsusb
Bus 002 Device 002: ID 059b:0177 Iomega Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0d8c:0201 C-Media Electronics, Inc. 
Bus 001 Device 004: ID 413c:3200 Dell Computer Corp. 
Bus 001 Device 003: ID 413c:2003 Dell Computer Corp. 
Bus 001 Device 002: ID 0c16:0001 Gyration, Inc. 
Bus 001 Device 001: ID 0000:0000  
```

```

```

```

```

---

### Post by tuxxy on 2008-08-07
Theres a couple of things to try here

[http://ubuntuforums.org/archive/index.php/t-590842.html](http://ubuntuforums.org/archive/index.php/t-590842.html)

---

### Post by Fen_Star on 2008-08-07
> **tuxxy said:**
> Theres a couple of things to try here

[http://ubuntuforums.org/archive/index.php/t-590842.html](http://ubuntuforums.org/archive/index.php/t-590842.html)I got alsamixer to work now, but still no sound. Is my best bet going to be buying a sound card?

---

### Post by gibz85 on 2008-10-10
Try opensuse... I know people think its evil... But it has the best hardware support and yast is way superior than any other tool...

As it is sais i have the same MB as yours...

In opensuse its suppported to the fullest... The soud is awesome... It even gives 7.1 wit 94khz...

Only thing you gotta do if ya using kde4 is update the opensuse alsa..

And it can easyly done with addind multimedia repositpry and updating...

If using gnome it works out of the box....

---

