---
title: "Any way to increase CD ripping speed?"
date: 2008-05-13
forum: Multimedia Software
---

### Post by danduq on 2008-05-13
Hi,

I've tried using Sound Juicer and RhythmBox to rip tracks from CD to MP3, but they seem pretty slow. Is there any way I can speed up the CD reading speed?

Ubuntu 8.04
Sound Juicer 2.22.0
RhythmBox 0.11.5

Thanks.

---

### Post by aeiah on 2008-05-13
its probably not the speed of the ripping, its the speed of the converting to mp3 that is taking a while. how long does it take and what are your pc specs? converting to mp3 relies on your cpu a lot

---

### Post by aeiah on 2008-05-13
if you have disk space to spare, you could perhaps rip everything to an uncompressed format from the cds, and then you can convert them all to mp3 and leave your pc unattended. it depends how much ripping you're doing though i guess.

---

### Post by danduq on 2008-05-13
> **aeiah said:**
> its probably not the speed of the ripping, its the speed of the converting to mp3 that is taking a while. how long does it take and what are your pc specs? converting to mp3 relies on your cpu a lot

At a guess it's ripping at approximately 2x normal speed.

Main PC specs are;
Dell Latitude D620
CPU: Intel(R) Core(TM)2 T7200 @ 2.00GHz
Memory:	2GiB

I also have a Windows partition on the same machine (dual boot) and Winamp will easily tear through a CD at 10-12x, so the H/W is capable.

Are there any test I can run?

Thanks.

---

### Post by Eddie Wilson on 2008-05-13
Use grip and you will have great speeds. I went from 2x in Soundjuicer to 20x to 30x speed in grip. I removed Soundjuicer.

Eddie

---

### Post by danduq on 2008-05-14
> **Eddie Wilson said:**
> Use grip and you will have great speeds. I went from 2x in Soundjuicer to 20x to 30x speed in grip. I removed Soundjuicer.

Eddie

Cool, thanks. I installed Grip, also had to install lame. CD ripping was still only about 2x until I disabled cdparanoia. Now it's much faster, thanks!

---

### Post by hollowhead on 2008-05-14
I use grip with CDparanoia for saety reasons.  It is great at recovering really scratched CD's as well.

---

### Post by danduq on 2008-05-15
Booooo. I just tried ripping another CD with Grip, and even with cdparanoia disabled it was only running around 2x. :(

Does anyone know of any way I can speed this up?

I read in the Grip manual that using SCSI emulation should improve speed. My device is /dev/cdrom, and the properties of this device say Connection: SCSI.

Any other ideas?

Thanks.

---

### Post by danduq on 2008-05-15
Further to this, I just ripped a track from a CD in good condition using Grip whilst watching Top.

Grips %CPU never rose above 9, and free memory was over 1GB.

---

### Post by SlaughterDog on 2008-10-06
I have two disc drives, and one rips fast, and one rips slow (the older of the two is the fast one), on Ubuntu. On Windows, they both rip at full speed. Both are 52x drives.


DMA seems to be enabled, doesn't it?
```
todd@computer:~$ hdparm -i /dev/scd0

/dev/scd0:

 Model=SONY    CD-RW  CRX320EE                 , FwRev=RYK4    , SerialNo=2006070800050450    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-5

 * signifies the current active mode

todd@computer:~$ hdparm -i /dev/scd1

/dev/scd1:

 Model=SONY    CD-RW  CRX220E1                 , FwRev=6YS1    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no

 * signifies the current active mode

todd@computer:~$ 

```

Edit: bringing up the properties for the drive in the file browser shows that they are SCSI connected, but indeed they are just ATAPI. I had this problem on Windows, and in fact it wouldn't let me burn, because of the drivers installed for the controller. I guess it has SCSI emulation or something; I'm not sure.

---

