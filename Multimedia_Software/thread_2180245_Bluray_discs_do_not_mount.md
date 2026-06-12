---
title: "Bluray discs do not mount"
date: 2013-10-12
forum: Multimedia Software
---

### Post by hannaman on 2013-10-12
Bluray worked fine on 13.04 and when I updated 13.04 to 13.10.  In order to get rid of my Windows7 partition completely, I installed 13.10 from scratch and formated the hard drive in the process. Now my Bluray discs can not be mounted.  The drive itself works.  Dvds and audio cds inserted into the drive work just fine.  I think this means that I need to install something to get bluray working, but I am not sure what at this point.  I have installed libbluray, libdvdcss2, etc.  I am not sure where to go from here.  Does any one have any idea of what I may be missing in my 13.10 installation so blurays will not mount or be read?
Here is some information:

```
michael@ubuntu:~$ wodim dev=/dev/sr1 --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sr1'	rwrw-- : 'ATAPI' 'iHES208   2'
-------------------------------------------------------------------------

```

```
michael@ubuntu:~$ modinfo udf
filename:       /lib/modules/3.11.0-11-generic/kernel/fs/udf/udf.ko
license:        GPL
description:    Universal Disk Format Filesystem
author:         Ben Fennema
alias:          fs-udf
srcversion:     B4F589503B9C1FFF2D00744
depends:        crc-itu-t
intree:         Y
vermagic:       3.11.0-11-generic SMP mod_unload modversions 

```

```
michael@ubuntu:~$ sudo mount -t udf /dev/sr1 /mnt
mount: no medium found on /dev/sr1

```

Thanks

---

### Post by hannaman on 2013-10-15
Updated information:
Blurays seem to randomly start working between updates, reboots and other factors I haven't figured out yet.  There is no pattern that I can see and if one does mount, when I eject the disc, I cannot mount it again or get another one to mount.
Not sure if this info is helpful and the randomness is frustrating.

---

