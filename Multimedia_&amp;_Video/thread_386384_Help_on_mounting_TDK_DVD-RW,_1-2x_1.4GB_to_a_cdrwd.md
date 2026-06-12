---
title: "Help on mounting TDK DVD-RW, 1-2x 1.4GB to a cdrw/dvdrom drive"
date: 2007-03-16
forum: Multimedia &amp; Video
---

### Post by andoty_jazz on 2007-03-16
**Hello everyone and Good Morning.**


If there's anyone out there who would want to help me mount a dvd-rw to my cdrw/dvdrom drive.


1.) When I insert the dvd-rw, it just reads the disk but nothing seems to happen.

2.) the disk full info. TDK DVD-RW, 1-2x 1.4GB, SCRATCHPROOF DATA/VIDEO

3.)When I mounted it manually

a.)  **mount /media/cdrom0**

*i get this message:* 
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

 b.) *dmesg | tail*
                           
[17201438.920000] cdrom: hdc: mrw address space DMA selected
[17201438.960000] cdrom: hdc: mrw address space DMA selected
[17201438.976000] attempt to access beyond end of device
[17201438.976000] hdc: rw=0, want=68, limit=4
[17201438.976000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[17201550.976000] cdrom: hdc: mrw address space DMA selected
[17201551.008000] cdrom: hdc: mrw address space DMA selected
[17201551.020000] attempt to access beyond end of device
[17201551.020000] hdc: rw=0, want=68, limit=4
[17201551.024000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16


b.) sudo mount /dev/hdc /media/cdrom

mount: block device /dev/hdc is write-protected, mounting read-only
mount: you must specify the filesystem type

c.) under my /etc/fstab
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


If there's any response of this issue, it will be greatly appreciated.

---

