---
title: "driveropts not set to burnfree when burning?"
date: 2008-04-28
forum: Multimedia Software
---

### Post by fiskking on 2008-04-28
Had no problems burning cd´s (only dvd´s)in the past but now driveropts is not set to burnfree?

In terminal I used ´cdrecord´,´hdparm´ to get more info on drives:

```
fisk@c-71-207-249-210:~$ cdrecord --devices
Beginning native device scan. This may take a while if devices are busy...
wodim: Overview of accessible drives (2 found) :
----------------------------------------------------------------------
0    dev='/dev/sr0'   rwrw-- :  'LITE-ON'  'LTR-24102M'
1    dev='/dev/sr1'   rwrw-- :  'HL-DT-ST'  'DVDRAM GSA-E40L'
----------------------------------------------------------------------
fisk@c-71-207-249-210:~$ hdparm /dev/sr0

/dev/sr0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

fisk@c-71-207-249-210:~$ hdparm /dev/sr1
/dev/sr1:
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device


```


Any help?

---

### Post by fiskking on 2008-04-28
bmp

---

