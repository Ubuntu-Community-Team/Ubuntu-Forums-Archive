---
title: "totem - dvd playback dropped frames audio out of sync"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by matva on 2007-01-05
totem plays dvds out of sync. dma is on:
```
/dev/hdc:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)

also:
john@8600:~$ sudo hdparm -t /dev/hdc

/dev/hdc:
 Timing buffered disk reads:    2 MB in  3.60 seconds = 569.36 kB/sec
BLKFLSBUF failed: Function not implemented

john@8600:~$ hdparm -i /dev/hdc

/dev/hdc:

 Model=_NEC DVD+/-RW ND-6500A, FwRev=2.24, SerialNo=
 Config={ Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no

 * signifies the current active mode

```

---

### Post by hotani on 2007-01-10
same problem here. totem/xine and gxine both are horribly out of sync. gstreamer won't even OPEN a DVD.

---

