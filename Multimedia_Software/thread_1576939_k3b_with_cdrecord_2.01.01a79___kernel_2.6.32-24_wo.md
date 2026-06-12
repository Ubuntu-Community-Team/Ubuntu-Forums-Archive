---
title: "k3b with cdrecord 2.01.01a79   kernel 2.6.32-24 won't burn ISO  CyberDrive CW078D"
date: 2010-09-18
forum: Multimedia Software
---

### Post by flyinfishy on 2010-09-18
Hey Everybody.
  I've been searching the forums to try and resolve my problem but I've been working this problem for weeks now and can't quite seem to make the connection. Here's what I've got:
I uninstalled wodim and manually installed cdrtools 2.01.01a79.  I created the symbolic links as specified to in [http://cdrecord.berlios.de/private/linux-dist.html](http://cdrecord.berlios.de/private/linux-dist.html)
and [http://ubuntuforums.org/showthread.php?p=5552123](http://ubuntuforums.org/showthread.php?p=5552123)
I still can't burn my ISO and I checked in the cdrecord's readme file and verified that my CyberDrive CW078D (Setup as IDE Secondary Master) burner is supported.  When I go to burn the ISO in K3b,  the burn dialog opens up and says burning with cdrecord.  The disc never spins up and after about 4.5 minutes K3b fails and give an error log.  After that I can't eject the disc and the mount doesn't show up in the filesystem.  Here's my error log from K3b:

Devices
-----------------------
CyberDrv CW078D CD-R/RW 140D (/dev/sr0, CD-R, CD-RW, CD-ROM) [CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R] [%7]

System
-----------------------
K3b Version: 1.91.0
KDE Version: 4.4.2 (KDE 4.4.2)
QT Version:  4.6.2
Kernel:      2.6.32-24-generic

Used versions
-----------------------
cdrecord: 2.1.1a79

cdrecord
-----------------------
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
SCSI buffer size: 64512
/usr/bin/cdrecord: Warning: Drive returned invalid buffer size.
/usr/bin/cdrecord: Warning: The DMA speed test has been skipped.
Cdrecord-ProDVD-ProBD-Clone 2.01.01a79 (i686-pc-linux-gnu) Copyright (C) 1995-2010 J&#65533;rg Schilling
TOC Type: 1 = CD-ROM
Using libscg version 'schily-0.9'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'CyberDrv'
Identifikation : 'CW078D CD-R/RW  '
Revision       : '140D'
Device seems to be: Generic mmc CD-RW.
Current: CD-R
Profile: CD-RW 
Profile: CD-R (current)
Profile: CD-ROM 
Profile: Removable Disk (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1806336 = 1764 KB
FIFO size      : 4194304 = 4096 KB
/usr/bin/cdrecord: Cannot load media.
Track 01: data   685 MB        
Total size:      787 MB (78:00.10) = 351008 sectors
Lout start:      787 MB (78:02/08) = 351008 sectors

cdrecord command:
-----------------------
/usr/bin/cdrecord -v gracetime=2 dev=/dev/sr0 speed=40 -sao driveropts=burnfree -data -tsize=351008s -

This is running on Ubuntu 10.04 LTS.  If anyone can help, I thank you in advance for your time and helpfulness.
Carl Fish

---

