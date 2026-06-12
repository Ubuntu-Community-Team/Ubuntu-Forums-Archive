---
title: "sound not working after new mobo"
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by Spartan.II.117 on 2007-09-09
i recently transferred my mom's hdd into a new machene, and the only thing i cant figure out is sound. it seems to detect the card but nothing will come out.
(7.04 intel motherboard ich5 with on board ac97 sound.)

---

### Post by pheeror on 2007-09-09
Hi,
If you have problems with hardware output of lspci -nn is often useful. When you try play sound in your favourite player, does it complain about no sound device or it seems like everything is ok, but no sound? Are you sure cables fit correctly?

Also try:
 ```

aplay somefile.wav
aplay -l

```

---

### Post by Spartan.II.117 on 2007-09-09
lspci -nn:
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
aplay does nothing, the hard drive was the only thing to change.

---

