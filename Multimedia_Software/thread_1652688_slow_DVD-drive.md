---
title: "slow DVD-drive"
date: 2010-12-25
forum: Multimedia Software
---

### Post by Vestigial on 2010-12-25
After DVDs, and CDs didnt play properly (playing,stop,playing,stop,playing... forgot the english word for that^^) on Maverick and on Lucid I tried to find a reason.

My DMA seems to be on
```
bice@bice:~$ sudo hdparm -i /dev/sr0
/dev/sr0:

 Model=RICOH DVD+RW MP5316DAG, FwRev=2.B9, SerialNo=
 Config={ Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=unknown, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no

 * signifies the current active mode
```

but my drive is pretty slow (in other forums I read, that it should be 10-20 times as much buffer):
```
bice@bice:~$ sudo hdparm -tT /dev/sr0

/dev/sr0:
 Timing cached reads:   664 MB in  2.00 seconds = 332.03 MB/sec
 Timing buffered disk reads:    8 MB in  3.39 seconds =   2.36 MB/sec
```

Does anyone have an idea, why my drive could be so slow?

---

### Post by Vestigial on 2010-12-27
Please, Im sure someone in here knows how to deal with it.

---

### Post by IWantFroyo on 2010-12-27
It says buffer is unknown. Check settings, and go to system-administration-additional drivers and check if you need another driver or something. If worst comes to worst, make sure nothing's screwed up in BIOS. You might be having a master-slave problem (dvd drive struggles for control with the hard drive).

---

### Post by Vestigial on 2010-12-28
Can't find a special driver for it.

And it's a slave to my well working master hard disk ;-)

---

