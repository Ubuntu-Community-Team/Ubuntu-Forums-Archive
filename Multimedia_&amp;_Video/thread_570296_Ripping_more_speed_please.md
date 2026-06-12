---
title: "Ripping: more speed please"
date: 2007-10-08
forum: Multimedia &amp; Video
---

### Post by Tlon on 2007-10-08
I am using Xubuntu Gutsy Beta, but I had this same problem with two different front-ends on feisty, both of which used lame.

Ripping and encoding a cd takes a really, really long time.  I think that something has to be wrong, as I've got a QX6700 with 4GB (3,25GB functional) of RAM.  At least, it never took this long on Windows.

I tried to check to see if I have DMA enabled.  Here's the console read-out:

martin@Eschaton:~$ sudo hdparm /dev/scd0

/dev/scd0:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
martin@Eschaton:~$ sudo hdparm -d1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

...

Grip console isn't showing any errors, but this shouldn't be taking a half an hour, given my equipment.  According to conky, my proc never goes higher than 5% and my RAM utilization never goes higher than 25% (these are system totals, not grip utilization) during the entire process.  Any ideas?

---

### Post by koleoptero on 2007-10-23
DIsable paranoia and extra paranoia etc in the setings of Grip. That will speed you up.

---

