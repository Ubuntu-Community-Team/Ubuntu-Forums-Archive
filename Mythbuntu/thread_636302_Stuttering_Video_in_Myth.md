---
title: "Stuttering Video in Myth"
date: 2007-12-09
forum: Mythbuntu
---

### Post by CaptainPatent on 2007-12-09
I have an interesting problem. For a while I was using a 40Gb Hdd to store recorded video and everything worked properly. I decided to upgrade to a larger hdd and installed a 320Gb hdd as a secondary drive. For some reason the newer and larger hdd cannot keep up with the video stream like the 40Gb drive could. The video now jumps every 3-5 seconds and is unwatchable. I tested different cables and IDE channels just in case, but nothing fixed the problem. Is there a problem with certain hard drives or is there a setting I need (for some strange reason) to record to a secondary drive? I'm going to try out installing my 200GB drive today and will post the results later, but until then any advice or help is much appreciated.

By the way I have an Athlon XP 1800+ with 512Mb ram and an ATI 9250 and an ATI TV Wonder 200 (a setup I don't reccommend) which was working well when recording to the 40Gb drive.

---

### Post by barney_1 on 2007-12-09
What filesystem are you using?  XFS is kind of the gold-standard for reading speed.  I can't think of a hardware reason that would cause this unless you have a defective component.

---

### Post by CaptainPatent on 2007-12-11
I'm using ext3 for both hard drives. I agree that there shouldn't be a hardware issue, but I'm still trying to pinpoint what the heck is going on.

---

### Post by arjay1 on 2007-12-13
Just a thought.  I am no expert at all this, but do you have DMA enabled for your new disk?  If not, that could make a big difference

RJ

---

### Post by CaptainPatent on 2007-12-14
The DMA mode should have been set properly. My 200 GB drive has been working in the place of the 320. The hard drive in question is a WD3200AAJB. If anyone else has this drive, can you confirm or deny whether your setup works without stuttering video, What file system you use, and whether your card is software or hardware encoded.

I'm beginning to think the memory requirements for this drive may be higher than my 200GB Segate drive and with a software encoded card and 512MB of SDRAM (yes, SDRAM) it may make all the difference in writing.

Note this only happens after about 50GB of data is recorded and slowly gets worse as it continues to record. I'm going to run hardware checks on the drive to make sure it's not in some way defective and I'll try to benchmark it under linux (although I don't know of any hdd benchmarks in linux).

This could be a problem with memory allocation or drivers for the drive, it could be a faulty hdd, it could be high memory requirements for the drive... but I'm pretty sure it is the drive as a 40GB and a 200GB have worked flawlessly.

---

### Post by arjay1 on 2007-12-14
Probably teaching my grandmother to suck eggs here, but it may help others. If you want to be sure that DMA is enabled, run:

```
hdparm -d /dev/hda
```. It should give you "using_dma = 1 (on)".

If it is off you can run:
```
hdparm -d 1 /dev/hda
``` to turn it on.

You may have to precede these commands with /sbin/ and possibly run them as root.

For more diagnostic info you can run:

```
hdparm -i /dev/hda
```  This gives me:

```
Model=HL-DT-ST GCE-8400B, FwRev=B104, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
```

If you want to test the performance of a single drive, with or without DMA - or you want to compare results for two or more drives (which you might want to do) run this test:
```
/sbin/hdparm -t -T /dev/sda
```.  This gives me;

```
/dev/sda:
 Timing cached reads:   3316 MB in  2.00 seconds = 1657.90 MB/sec
 Timing buffered disk reads:  198 MB in  3.02 seconds =  65.47 MB/sec
```


Hope this helps someone!

RJ

---

