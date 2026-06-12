---
title: "Problems with DVD burning on Gutsy"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by wampirek on 2007-10-22
Hello, 

I've installed Gutsy few days ago and have problems with burning DVDs. 
I have NEC recorder (speed 16x) and good DVDs (also speed 16x), but burning a DVD takes about 15-20 minutes and it goes with 2-5x speed, no matter what programme I use. 
I have DMA enabled so I don't know what could be the problem... 

Please, help!

---

### Post by prshah on 2007-10-23
Hi there...

Looks to me to be a DMA problem only. What is the hardware config? Eg, how many drives? IDE? 40-pin or 80-pin cable? Master/Slave? Is the recorded DVD readable? What program did you use?

Better post output of `dmesg|grep DMA`, maybe it may give a clue?

Cheers,
PRS

---

### Post by wampirek on 2007-10-24
> **prshah said:**
> Hi there...

Looks to me to be a DMA problem only. What is the hardware config? Eg, how many drives? IDE? 40-pin or 80-pin cable? Master/Slave? Is the recorded DVD readable? What program did you use?

Better post output of `dmesg|grep DMA`, maybe it may give a clue?

Cheers,
PRS

I have 3 ATA hard drives and 1 CD/DVD recorder. The recorder is Slave. Yes, it reads everything with no problems. The program I use doesn't matter - Gnome Baker, Brasero, K3B... Nero also has some problems - it starts fast, but after a while it slows down and sometimes stops at all... 

```

wampirek@wampirek:~$ dmesg|grep DMA
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[   19.803283] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
[   19.803294]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   19.803307]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   21.254152] hda: 117231408 sectors (60022 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   21.290494] hdb: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[   21.333236] hdc: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(100)
[   21.410802] hdd: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)

```

It would be great if you could figure something out... 

Best Regards, 
Wampirek

---

### Post by wampirek on 2007-10-30
Really noone knows the answer?

---

### Post by kamonn on 2007-11-02
I updated from Feisty (in which I never had any problem burning dvds) to Gutsy and now I cannot burn dvds anymore. K3b and Gnome Baker fail. So far I've lost 3 discs :(

---

