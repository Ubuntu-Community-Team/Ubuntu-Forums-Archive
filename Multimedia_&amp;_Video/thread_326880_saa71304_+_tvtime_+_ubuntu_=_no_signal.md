---
title: "saa7130/4 + tvtime + ubuntu = no signal"
date: 2006-12-28
forum: Multimedia &amp; Video
---

### Post by Storo on 2006-12-28
First i'm from croatia and my englis isn't good. :( 

Now i haw some tv card (PCI) with saa7130 chiset and philips tv tuner. This card work in windows perfectly.

My problem is that when i start tvtime i get message "**no signal**" for tv-tuner, but my conposit tv-in works fine with my camera.

my dmesg | grep saa7134 shows

```
storo@storo:~$ dmesg | grep saa7130
[17179587.216000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179587.768000] saa7130[0]: found at 0000:01:01.0, rev: 1, irq: 98, latency: 64, mmio: 0xfbfffc00
[17179587.768000] saa7130[0]: subsystem: 19d0:0138, board: Kworld/KuroutoShikou SAA7130-TVPCI [card=10,insmod option]
[17179587.768000] saa7130[0]: board init: gpio is 39100
[17179587.904000] saa7130[0]: i2c eeprom 00: d0 19 38 01 10 28 ff ff ff ff ff ff ff ff ff ff
[17179587.904000] saa7130[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.904000] saa7130[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.904000] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.904000] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.904000] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.904000] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.904000] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.920000] tuner 0-0061: chip found @ 0xc2 (saa7130[0])
[17179587.928000] tuner 0-0063: chip found @ 0xc6 (saa7130[0])
[17179587.928000] saa7130[0]: registered device video0 [v4l2]
[17179587.928000] saa7130[0]: registered device vbi0
[17179588.184000] saa7130[0]/alsa: saa7130[0] at 0xfbfffc00 irq 98 registered as card -1
storo@storo:~$ 

```

dmesg | grep tuner

```
storo@storo:~$ dmesg | grep tuner
[[17180239.580000] tuner 0-0061: chip found @ 0xc2 (saa7130[0])
[17180239.580000] tuner 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[17180239.588000] tuner 0-0063: chip found @ 0xc6 (saa7130[0])

```

So if anyone have some hint it will be grate!

Thx!

P.S. Ina Croatia is PAL standard not NTSC.

---

### Post by scto on 2006-12-28
Hi,

please have a look here:
[http://linuxtv.org/repo/](http://linuxtv.org/repo/)

Newest v4l drivers, much more actual.

you need Mercurial, should be in the universe repo.

cheers
Tom

---

### Post by Storo on 2006-12-28
THX! 

I'll give a try!

---

### Post by scto on 2006-12-28
or here:
[http://www.linuxtv.org/wiki/index.php/How_to_install_DVB#Solution_with_v4l_manual_installation](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB#Solution_with_v4l_manual_installation)

Cheers
Tom

---

### Post by scto on 2006-12-28
And here's a Wiki entry about saa7130/4 cards:
[http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)

Cheers
Tom

---

