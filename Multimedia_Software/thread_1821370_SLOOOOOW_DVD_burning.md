---
title: "SLOOOOOW DVD burning"
date: 2011-08-09
forum: Multimedia Software
---

### Post by LuridCinema on 2011-08-09
Im getting 2x at most DVD burning. Quite often in Turbojet2 or using growisofs or whatever, Im getting even 0.5x DVD burning speeds.
I set the burn speed to 12x on Turbojet, but it hovers from 0.5x to maybe bursts of 5x.
I will get maybe 9 minute burn times in Brasero but 15 to 25 minutes in Turbojet2 and longer using growisofs or other CLI burning.

Im running 11.04 on a box w/ SATA drives, SATA DVD-RW's 12gb of Ram an Intel I-5 4 core processor

I have played w/ hdparm settings but no luck...I tried the below

```
root@p9-TH55-HD:/media/2tb# **hdparm -d1 -c1 -a8 -u1 /dev/sr2**

/dev/sr2:
 setting fs readahead to 8
 setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 setting unmaskirq to 1 (on)
 HDIO_SET_UNMASKINTR failed: Inappropriate ioctl for device
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 IO_support    =  0 (default) 
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 readahead     =  8 (on)

```I tried 
Adding the following to the end of your hdparm.conf 
/dev/hdc { dma = on }

NOTHING works !! GRRRRR

any ideas ???

---

### Post by LuridCinema on 2011-08-09
Im finding that w/ SATA drives **sdparm** is the controlling factor...too bad it's mostly greek for me

---

### Post by LuridCinema on 2011-08-09
Would a SATA controller card solve this ? Too bad I cannot just open up 3 instances of Brasero . I think the main issue is when burning multiple copies, it slows things down

---

