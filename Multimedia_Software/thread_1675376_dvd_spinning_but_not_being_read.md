---
title: "dvd spinning but not being read"
date: 2011-01-25
forum: Multimedia Software
---

### Post by jamaas on 2011-01-25
Old story I realise, please point me in the right direction to diagnose.  New Dell PC, 64 bit running 9.10, all updated.  I put in a dvd that used to work and has lots of picture images on it, disk spins but does not mount.  Any suggestions as to how to debug, or copy the stuff off the dvd most welcome.

Thanks

J

---

### Post by tommcd on 2011-01-25
> **jamaas said:**
>  I put in a dvd .. disk spins but does not mount.  Any suggestions as to how to debug, or copy the stuff off the dvd most welcome.

Do other DVD and CD discs work ok? Is it just this one DVD disc that will not mount? Or do you have problems with other optical media?

---

### Post by jamaas on 2011-01-26
Thanks Tommcd,

The drive seems to work in general, will play music cd's and movie dvd's, in this case this is a self recorded dvd with images from an artwork course.  Recorded about a year ago and worked at the time.  Could I be missing a codec or something?

Thanks

J

---

### Post by tommcd on 2011-01-26
> **jamaas said:**
> 
... in this case this is a self recorded dvd with images from an artwork course.  Recorded about a year ago and worked at the time.
Recordable DVDs can "go bad" (for lack of a more technical term). If all other discs work fine I would assume the one DVD is corrupted or faulty or something.
> **jamaas said:**
> 
  Could I be missing a codec or something?

A missing codec could prevent you from playing the media, but that would not prevent you from mounting the disc.
Try running **dmesg** in the teminal and note what the last line in the output is. Then put in the problematic DVD and run dmesg again and look at the last output. When I put in a recorded DVD and run dmesg the last 2 lines are:
```
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A

```
The "*ISO 9660 Extensions: Microsoft Joliet Level 3*" indicates the system recognizes the disc. You should get something similar to that.

---

