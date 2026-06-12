---
title: "Read problem with large dvd's"
date: 2008-11-15
forum: Multimedia Software
---

### Post by damalema on 2008-11-15
Hi,

I have a problem with reading double layer dvd's.

The dvd works for the first part. (thats why I figure it's a problem with double layer).

The size looks ok when it is mounted:
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/scd0              8256476   8256476         0 100% /media/DVD

Using fdisk gives another size:
Command (m for help): p
Disk /dev/scd0: 3934 MB, 3934234624 bytes

Dmesg tells me after trying to read certain files:
[48186.638640] sr0: rw=0, want=15290292, limit=7684052
[48186.638650] attempt to access beyond end of device

Output from when dvd-player is found:
[    6.048838] sd 2:0:0:0: [sdb] Attached SCSI disk
[    6.120351] ata5.00: ATAPI: _NEC DVD_RW ND-4570A, 1.02, max UDMA/33
[    6.136293] ata5.00: configured for UDMA/33
[    6.305127] scsi 4:0:0:0: CD-ROM            _NEC     DVD_RW ND-4570A  1.02 PQ: 0 ANSI: 5
[    6.305285] scsi 4:0:0:0: Attached scsi generic sg2 type 5
[    6.362460] Driver 'sr' needs updating - please use bus_type methods
[    6.367427] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.367432] Uniform CD-ROM driver Revision: 3.20

Any ideas?

/Dama

---

