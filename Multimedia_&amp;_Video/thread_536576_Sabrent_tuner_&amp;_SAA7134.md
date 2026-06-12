---
title: "Sabrent tuner &amp; SAA7134"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by lesemi on 2007-08-27
I have been trying to get this card going for quite a while - under Dapper - there was nothing that worked.
After many searches i have searched all treads and to no avail. 

my modprob.conf: 
options saa7134 card=42 tuner=17
my dmesg | grep saa
[   16.116000] saa7130[0]: board init: gpio is 80c000
[   16.220000] saa7130[0]: Huh, no eeprom present (err=-5)?
[   16.260000] tuner 2-0060: chip found @ 0xc0 (saa7130[0])
[   16.268000] tuner 2-0061: chip found @ 0xc2 (saa7130[0])
[   16.288000] saa7130[0]: registered device video0 [v4l2]
[   16.288000] saa7130[0]: registered device vbi0
[   16.288000] saa7130[0]: registered device radio0
[   16.400000] saa7134 ALSA driver for DMA sound loaded
[   16.400000] saa7130[0]/alsa: saa7130[0] at 0xd4011000 irq 21 registered as card -2


I have tried xawtv and tvtuner - i get a bit of muffled sound but a dark screen and that's it.

Any suggestions is appreciated. 
I have googled this issue and came across some info that there is a bug in saa7134 regarding this particular tuner - not sure if true... i recently installed fresh gutsy kubuntu.. (very nice by the way!) and still have same problem.

---

### Post by medya on 2007-08-30
use tuner 69 , and xawtv sucks, use kdetv.

---

