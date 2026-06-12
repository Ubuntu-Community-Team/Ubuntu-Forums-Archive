---
title: "choppy dvd playback 8.10"
date: 2009-04-25
forum: Mythbuntu
---

### Post by nrune on 2009-04-25
I am having some choppy dvd playback issues Under 8.04 the dvd drive was mounted under /dev/hcd0 under 8.10 it is mounted under /dev/sr0.  There are some changes to the way the dvd device is handled between 8.04 and 8.10.  

So I have switched playback profiles, tried vlc,mplayer etc and everything is choppy. I believe that I have narrowed it down to the dvd drive. I have changed bios settings from auto to udma2 and udma1 and I have changed ide cables. I know that this was working fine in 8.04. So I do I increase the speed of the dvd drive.  

hdparm
> 
/dev/sr0:

 Model=PLEXTOR DVDR   PX-712A                  , FwRev=1.07    , SerialNo=              430392
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no

 * signifies the current active mode
 

sudo hdparm -Tt /dev/sr0
> 
/dev/sr0:
 Timing cached reads:   320 MB in  2.00 seconds = 159.78 MB/sec
 Timing buffered disk reads:    6 MB in  3.95 seconds =   1.52 MB/se

dmesg | grep /dev/sr0
> [194234.425973] Buffer I/O error on device sr0, logical block 2376
[194234.425978] Buffer I/O error on device sr0, logical block 2377
[194234.425984] Buffer I/O error on device sr0, logical block 2378
[194234.425989] Buffer I/O error on device sr0, logical block 2379
[194234.524178] end_request: I/O error, dev sr0, sector 9688
[194234.626412] end_request: I/O error, dev sr0, sector 9736


Help!

---

### Post by nrune on 2009-04-26
And then I found this...

```
[    5.636461] ata6.00: ATAPI: PLEXTOR DVDR   PX-712A, 1.07, max UDMA/33
[    5.636472] ata6.00: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[    5.636475] ata6.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    5.644408] ata6.00: configured for UDMA/33
[    6.075144] EXT3-fs: mounted filesystem with ordered data mode.
```

DMA does seem to be the central issue.

---

### Post by nrune on 2009-04-26
Which led me to 

> On Intrepid using adding "pata_ali atapi_dma=1" at the end of /etc/initramfs-tools/modules

sudo gedit /etc/initramfs-tools/modules

and running

sudo update-initramfs -u


a reboot and it's fixed!!

---

