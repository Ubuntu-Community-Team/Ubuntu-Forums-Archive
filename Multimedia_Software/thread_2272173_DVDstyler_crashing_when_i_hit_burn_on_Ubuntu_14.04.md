---
title: "DVDstyler crashing when i hit burn on Ubuntu 14.04"
date: 2015-04-04
forum: Multimedia Software
---

### Post by hectorsales on 2015-04-04
I have installed **dvdstyler 2.5.2-0ubuntu3 0** and i when press start to it works for a split second the just disappears.

 **To re-produce**


     
[LIST]
[*]I open dvdstyler. 
[*]I adding a Video File (Project). 
[*]I press the button Burn (option e.g create "dvd.iso") 
[*]I press start ..and dvdstyler it closes abruptly. 
[/LIST]


If** i open dvdstyler from the terminal**, i get this error before close UI:

```
$ dvdstyler
```

> Output #0, dvd, to '/tmp/dvd-tmp/menu1-0.mpg_bg.mpg':
    Stream #0.0: Video: mpeg2video, yuv420p, 720x576 [PAR 16:15 DAR 4:3], q=2-31, 6000 kb/s, 90k tbn, 25 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 2 channels, s16, 64 kb/s
[ac3 @ 0x1debfc0] channel_layout not specified
[ac3 @ 0x1debfc0] No channel layout specified. The encoder will guess the layout, but it might be incorrect.
[dvd muxer @ 0x273b680] Value 10080000.000000 for parameter 'muxrate' out of range
[dvd muxer @ 0x273b680] Error setting option muxrate to value 10080000.

The version **of dvdstyler is  2.5.2-0ubuntu3 on Ubuntu 14.04 LTS Trusty.**

Any suggestion to fix this ..

**Note**: I open a bug report on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/dvdstyler/+bug/1440374](https://bugs.launchpad.net/ubuntu/+source/dvdstyler/+bug/1440374)

Regards.

---

### Post by daniel261 on 2015-04-08
it works from a reboot

---

### Post by slougheed-bcs on 2015-04-09
Same problem here. I've tried many things, from trying to add missing codecs using a PPA. Many reboots, still crashing. Brasero won't burn a Video DVD either. It's likely codec related, and both programs suffering from the same bug. 

I'm trying to burn a .mpg to video DVD.

---

### Post by mc4man on 2015-04-09
2.5.x is broken, (segfault, ck. /var/crash/ for reason)
2.7.x is broken, will try to create a 4.3Gb menu, then hang
Best bet is to find a 2.9.x build

---

