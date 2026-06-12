---
title: "[SOLVED] Can't write DVD"
date: 2007-12-18
forum: Multimedia Production
---

### Post by evil316 on 2007-12-18
I have some .avi files I want to write to DVD so it can be played on my DVD player.  I used DeVeDe and added what amounted to 1.2 gig of .avi files.  The blank DVD is a DVD-R 4.7gig.  When I put the DVD in the system recognizes it but that's as far as I get.  I created an iso image with DeVeDe ready to burn to disk.  I open CD/DVD creater in my places and place my iso image in it.  I then chose write to disk and create from image.  When I do that I get 2 choices for write disc to: one is file image and the other is IL-DU-STEVERSW!GSA-H30M!!!!!!!!.  My DVD drive doesn't show up.  Disc name is greyed out, data size is set to 2.8 gig and cannot be changed and write speed is set to max and cannot be changed either.  

Here is what my /etc/fstab file looks like:
----------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4663f147-4e37-4d40-8883-ebfc72c0efa9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=5a644d5d-097f-4ade-b981-e2a509687e4f none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
------------------------------------------------------------
Thanks in advance for any advice or ideas!

---

### Post by evil316 on 2007-12-18
From command line I type:

sudo growisofs -dvd-compat -Z /dev/dvd= YGG_S1_E_1-4,_6-8.iso

I get:

:-( unable to open64("",O_RDONLY): No such file or directory

---

### Post by evil316 on 2007-12-18
I also try this command:

darren@ubuntu-desktop:~$ dmesg | grep -i cd | grep -i rom
[   15.396517] hda: IL-DU-STEVERSW!GSA-H30M ! ! ! ! ! ! ! !, ATAPI CD/DVD-ROM drive
[   15.754357] hda: ATAPI 40X DVD-ROM DVD-R-RAM CD/RW drive, 2048kB Cache, UDMA(33)
[   15.754365] Uniform CD-ROM driver Revision: 3.20
[   36.332055] cdrom: This disc doesn't have any tracks I recognize!
darren@ubuntu-desktop:~$ 


When I attempt to write my screen goes wacko and I just get a weird pattern and I have to reboot to get my desktop back.  The DVD light never comes on.  When it boots back up it says it was unable to write because no files were selected.

---

### Post by evil316 on 2007-12-18
I've tried a different dvd and now it says it doesn't even recognize there is a DVD available to burn.

---

### Post by evil316 on 2007-12-18
tried this too:

darren@ubuntu-desktop:~$ sudo cdrecord dev=/dev/cdrom driveropts=burnfree -v -data YGG_S1_E_1-4,_6-8.iso
cdrecord: No write mode specified.
cdrecord: Asuming -sao mode.
cdrecord: If your drive does not accept -sao, try -tao.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
TOC Type: 1 = CD-ROM
scsidev: '/dev/cdrom'
devname: '/dev/cdrom'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'schily-0.9'.
Driveropts: 'burnfree'
SCSI buffer size: 64512
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT,ST'
Identifikation : 'DVDRRV FS@-H20L '
Revision       : 'S642'
Device seems to be: Generic CD-ROM.
cdrecord: Sorry, no CD/DVD/BD-Recorder or unsupported CD/DVD/BD-Recorder found on this target.
Using generic SCSI-2       CD-ROM driver (scsi2_cd).
Driver flags   : 
Supported modes: 
Drive pbuf size: 134217728 = 131072 KB
cdrecord: Success. read buffer: scsi sendcmd: no error
CDB:  3C 00 00 00 00 00 00 FC 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 08 02 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x02 (logical unit communication parity error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 64512
cmd finished after 0.001s timeout 200s
FIFO size      : 4194304 = 4096 KB
cdrecord: Drive does not support SAO recording.
cdrecord: Illegal write mode for this drive.
darren@ubuntu-desktop:~$

---

### Post by evil316 on 2007-12-18
I can't even read DVDs.  I put in my Ubuntu DVD and it it shows up as a blank DVD.

---

### Post by evil316 on 2007-12-18
I installed some additional packages and now when attempting to write a dvd with 1gig of data in gnomebacker I get:

:-( FORMAT allocaion length isn't sane

or at the CLI I get:

darren@ubuntu-desktop:~$ sudo cdrecord dev=/dev/cdrom driveropts=burnfree -v -data gnomebaker.iso
cdrecord: No write mode specified.
cdrecord: Asuming -sao mode.
cdrecord: If your drive does not accept -sao, try -tao.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
TOC Type: 1 = CD-ROM
scsidev: '/dev/cdrom'
devname: '/dev/cdrom'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'schily-0.9'.
Driveropts: 'burnfree'
SCSI buffer size: 64512
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT,ST'
Identifikation : 'DVDRRV FS@-H20L '
Revision       : 'S642'
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Current: DVD+RW
Profile: DVD-RAM 
Profile: DVD+RW/DL 
Profile: DVD+RW (current)
Profile: DVD+RW 
Profile: DVD-R/DL layer jump recording 
Profile: DVD-RW sequential recording 
Profile: DVD-RW sequential recording 
Profile: DVD-RAM 
Profile: DVD-ROM 
Profile: DVD-ROM 
Profile: CD-RW 
Profile: Reserved 
Profile: Reserved 
Profile: Reserved 
resid: 16
Using generic SCSI-3/mmc-3 DVD+RW driver (mmc_dvdplusrw).
Driver flags   : NO-CD DVD MMC-3 SWABAUDIO BURNFREE 
Supported modes: PACKET SAO LAYER_JUMP
Drive buf size : 1343488 = 1312 KB
Drive pbuf size: 134217728 = 131072 KB
resid: 62448
FIFO size      : 4194304 = 4096 KB
Track 01: data  1030 MB        
Total size:     1030 MB = 527692 sectors
Current Secsize: 2048
resid: 8
resid: 8
cdrecord: Success. read track info: scsi sendcmd: no error
CDB:  52 00 00 00 00 00 00 00 04 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 4
cmd finished after 0.001s timeout 240s
cdrecord: Data will not fit on any disk.
cdrecord: Cannot write more than remaining DVD/BD capacity.
darren@ubuntu-desktop:~$

---

### Post by evil316 on 2007-12-18
The laptop I have for my wife that has Ubuntu on it burns the same files perfectly fine.  My PC won't even recognize the sondy DVD-R blank DVD's but they burn fine on the laptop.  Please any help would be very much appreciated.

---

### Post by boknoy_ph on 2007-12-19
it seems to be you were talking all by yourself here.

have you tried if your DVD burner is physically working, ie, burn data using windows?

---

### Post by eye208 on 2007-12-19
> **evil316 said:**
> [   15.396517] hda: IL-DU-STEVERSW!GSA-H30M ! ! ! ! ! ! ! !, ATAPI CD/DVD-ROM drive
"IL-DU-STEVERSW!GSA-H30M ! ! ! ! ! ! ! !" is quite a funny name for a DVD drive. If the firmware of the drive has been hacked (e.g. to make it region-free) it might just be broken now.

---

### Post by evil316 on 2007-12-19
The drive worked fine under windows previously.  I never hacked the drive and the firmware should not have been changed since I purchased the system at Walmart.  Could some sort of package I added hacked the drives firmware?  I think since it already isn't working I'll try new firmware on it and if that doesn't work I'll just swap it out with something else.

Here's something else.  I'm pretty sure the DVD drive is SATA.  Do those drives have problems with Ubuntu?  If that's the case what's my best option?  External USB drive?  A different SATA drive that is known to work with Linux?  Some sort of converter card?

---

### Post by evil316 on 2007-12-19
I solved the problem.  I swapped the DVD player out with another one and it works.  Probably was some sort of firmware issue but I don't know why.

---

