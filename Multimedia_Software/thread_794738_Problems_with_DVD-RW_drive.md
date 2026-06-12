---
title: "Problems with DVD-RW drive"
date: 2008-05-14
forum: Multimedia Software
---

### Post by Devz0r on 2008-05-14
Usually, discs that were put into my DVD-RW drive won't show up in Ubuntu.  When they do show up, I try to burn something on them, and it takes forever and is pretty inconsistent.

[Here's]("http://www.youtube.com/watch?v=VlWF0JmUR_g") a video of me burning a DVD ISO.

---

### Post by mc4man on 2008-05-14
What is the brand of your blank media and model,age of your dvd drive

---

### Post by Devz0r on 2008-05-14
> **mc4man said:**
> What is the brand of your blank media and model,age of your dvd drive
Discs - imation 8x 4.7 GB
Burner - [http://www.newegg.com/product/product.aspx?Item=N82E16827151136](http://www.newegg.com/product/product.aspx?Item=N82E16827151136)

---

### Post by mc4man on 2008-05-14
+r or -r ? Asking because that model has had issues with -r's
ck. hdparm -i /dev/scd0     scd0 = drive in question yours may be different (ck fstab if you don't know)
Your burn speed <1x is so slow hard to believe it's a dma issue
When was the last time you had good burn speeds ie. a dvd5 @ 4x should take about 12 min.

edit : does this resemble your situation, about 2/3 down page
[http://shekel.blogspot.com/2007_05_01_archive.html](http://shekel.blogspot.com/2007_05_01_archive.html)

---

### Post by Devz0r on 2008-05-14
> **mc4man said:**
> +r or -r ? Asking because that model has had issues with -r's
I think it is +r.
> 
ck. hdparm -i /dev/scd0     scd0 = drive in question yours may be different (ck fstab if you don't know)
```
/dev/scd0:

 Model=TSSTcorpCD/DVDW SH-S182M                , FwRev=SB03    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 *udma1 udma2 
 AdvancedPM=no

 * signifies the current active mode

```
> 
Your burn speed <1x is so slow hard to believe it's a dma issue
When was the last time you had good burn speeds ie. a dvd5 @ 4x should take about 12 min.
I don't really remember...  It has been a while.
> 
edit : does this resemble your situation, about 2/3 down page
[http://shekel.blogspot.com/2007_05_01_archive.html](http://shekel.blogspot.com/2007_05_01_archive.html)
Yes.  I am going to go check and see if it works in Windows... as soon as I find an ISO burner for it.

---

### Post by Devz0r on 2008-05-15
It's doing it in Windows, too.  The write buffer is going from 0% to 100% every other second.

---

### Post by mc4man on 2008-05-15
Time for a new drive

---

