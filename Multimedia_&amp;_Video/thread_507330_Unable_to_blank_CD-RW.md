---
title: "Unable to blank CD-RW"
date: 2007-07-22
forum: Multimedia &amp; Video
---

### Post by satimis on 2007-07-22
Hi folks,

Ubuntu Desktop 7.04
Gnome desktop
k3b

I have tried more than an hour and can't erase the CDRW nor to burn iso image on it by force.

Start K3b  as user.  On inserting the CDRW on the tray it mounts automatically.  I select [force] to burn it.  Failed with warning```

.....
Blanking PMA, TOC, pregap
Errno: 0 (Success), blank unit scsi sendcmd: no error
CDB:  A1 01 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 12 00 00 00 01 27 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x27 Qual 0x00 (write protected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.009s timeout 9600s
/usr/bin/wodim: Cannot blank disk, aborting.
/usr/bin/wodim: Some drives do not support all blank types.
/usr/bin/wodim: Try again with wodim blank=all.

```


On terminal;
# wodim blank=all```

Quickly guessing the name of a drive capable to write CD-R, please wait...
Found /dev/cdrw, assuming dev=/dev/cdrw
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'SONY    '
Identification : 'CD-RW  CRX160E  '
Revision       : '1.0e'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Speed set to 1411 KB/s
Starting to write CD/DVD at speed   8.0 in real BLANK mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
Errno: 0 (Success), blank unit scsi sendcmd: no error
CDB:  A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 12 00 00 00 01 27 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x27 Qual 0x00 (write protected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.013s timeout 9600s
wodim: Cannot blank disk, aborting.
root@ubuntu704:/home/satimis# wodim blank=all
Quickly guessing the name of a drive capable to write CD-R, please wait...
Found /dev/cdrw, assuming dev=/dev/cdrw
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'SONY    '
Identification : 'CD-RW  CRX160E  '
Revision       : '1.0e'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Speed set to 1411 KB/s
Starting to write CD/DVD at speed   8.0 in real BLANK mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
Errno: 0 (Success), blank unit scsi sendcmd: no error
CDB:  A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 12 00 00 00 01 27 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x27 Qual 0x00 (write protected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.004s timeout 9600s
wodim: Cannot blank disk, aborting.

```

$ wodim --devices```

Beginning native device scan. This may take a while if devices are busy...

```
It hangs there for prolonged time with/without CDRW on the tray.


Please help.  TIA


B.R.
satimis

---

### Post by tbroderick on 2007-07-23
Check your /etc/fstab for the a line like;
```

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Note the /dev/*xxx*. That is your CD drive. Next try running wodim as sudo and using your CD drive /dev location. Example;
```

sudo wodim dev=/dev/hdc blank=all
```

---

### Post by satimis on 2007-07-23
Hi tbroderick;

> Check your /etc/fstab for the a line like;
```

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Note the /dev/*xxx*. That is your CD drive. Next try running wodim as sudo and using your CD drive /dev location. Example;
```

sudo wodim dev=/dev/hdc blank=all
```
Found following line```

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

$ wodim --devices```

Beginning native device scan. This may take a while if devices are busy...
wodim: Overview of accessible drives (2 found) :
----------------------------------------------------------------------
0    dev='/dev/hda'   rwrw-- :  'SONY'  'CD-RW  CRX160E'
1    dev='/dev/hdc'   rwrw-- :  'MATSHITA'  'CD-ROM CR-593'
----------------------------------------------------------------------

```

$ sudo wodim dev=/dev/hda blank=all```

Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'SONY    '
Identification : 'CD-RW  CRX160E  '
Revision       : '1.0e'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Speed set to 1411 KB/s
Starting to write CD/DVD at speed   8.0 in real BLANK mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
Errno: 0 (Success), blank unit scsi sendcmd: no error
CDB:  A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 12 00 00 00 01 27 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x27 Qual 0x00 (write protected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.003s timeout 9600s
wodim: Cannot blank disk, aborting.

```


Failed.


Edit:
Burning iso image on CD-RW works w/o problem.

I think this is a bug;

Bug #114122 in cdrkit (Ubuntu)
Burner not working in 7,04
[https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/114122](https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/114122)


satimis

---

