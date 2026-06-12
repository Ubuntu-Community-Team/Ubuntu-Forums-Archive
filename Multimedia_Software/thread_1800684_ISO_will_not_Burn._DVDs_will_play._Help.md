---
title: "ISO will not Burn. DVDs will play. Help?"
date: 2011-07-09
forum: Multimedia Software
---

### Post by MSetty on 2011-07-09
I created the images with DeVeDe. I was able to burn 1 image with Brasero. Subsequent attempts have resulted in an error. Here is my K3b Error Log.

```
Devices
-----------------------
PIONEER DVD-RW  DVR-K17A 1.50 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite] [%7]

System
-----------------------
K3b Version: 2.0.1
KDE Version: 4.5.5 (KDE 4.5.5)
QT Version:  4.7.0
Kernel:      2.6.35-30-generic

Used versions
-----------------------
cdrecord: 3.0

cdrecord
-----------------------
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
SCSI buffer size: 64512
/usr/bin/cdrecord: Warning: Cannot read drive buffer.
/usr/bin/cdrecord: Warning: The DMA speed test has been skipped.
Cdrecord-ProDVD-ProBD-Clone 3.00 (i686-pc-linux-gnu) Copyright (C) 1995-2010 J&#65533;rg Schilling
TOC Type: 1 = CD-ROM
Using libscg version 'schily-0.9'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identifikation : 'DVD-RW  DVR-K17A'
Revision       : '1.50'
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Current: DVD-RW sequential recording
Profile: DVD+R/DL 
Profile: DVD+R 
Profile: DVD+RW 
Profile: DVD-R/DL sequential recording 
Profile: DVD-RW sequential recording (current)
Profile: DVD-RW restricted overwrite (current)
Profile: DVD-RAM 
Profile: Removable Disk 
Profile: DVD-R sequential recording (current)
Profile: DVD-ROM 
Profile: CD-RW 
Profile: CD-R 
Profile: CD-ROM 
Using generic SCSI-3/mmc-2 DVD-R/DVD-RW/DVD-RAM driver (mmc_dvd).
Driver flags   : NO-CD DVD MMC-3 SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1605632 = 1568 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data  2502 MB        
Total size:     2502 MB = 1281292 sectors
Current Secsize: 2048
Total power on  hours: 75040
Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 1017204
Reducing transfer size from 64512 to 32768 bytes.
Starting to write CD/DVD/BD at speed 2 in real SAO mode for single session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Starting new track at sector: 0
Track 01:    0 of 2502 MB written.
Track 01:    1 of 2502 MB written (fifo  92%)  13.1x.
/usr/bin/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 03 10 00 00 10 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 71 00 04 00 00 00 00 0E 00 00 00 00 44 D9 00 00
Sense Key: 0x4 Hardware Error, deferred error, Segment 0
Sense Code: 0x44 Qual 0xD9 (internal target failure) [No matching qualifier] Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 200s
/usr/bin/cdrecord: A write error occured.
/usr/bin/cdrecord: Please properly read the error message above.
write track data: error after 1605632 bytes
Writing  time:   55.502s
Average write speed  34.2x.
Fixating...
Fixating time:    0.005s
/usr/bin/cdrecord: fifo had 177 puts and 50 gets.
/usr/bin/cdrecord: fifo was 0 times empty and 2 times full, min fill was 89%.

cdrecord command:
-----------------------
/usr/bin/cdrecord -v gracetime=2 dev=/dev/sr0 speed=2 -sao driveropts=burnfree -data -tsize=1281292s -

```

---

### Post by ajgreeny on 2011-07-09
I have no idea whether it will help, but it is worth trying a burn at as slow a speed as you can rather than the high speed you used that time.

Apologies if that does not help.

---

### Post by MSetty on 2011-07-09
> **ajgreeny said:**
> I have no idea whether it will help, but it is worth trying a burn at as slow a speed as you can rather than the high speed you used that time.

Apologies if that does not help.

I don't understand the speed at the bottom of the log. I only tried to burn it at 2x speed

---

### Post by ajgreeny on 2011-07-09
I can't remember how to set the burn speed in k3b, but I do think you should try again, perhaps at 4x speed.  Maybe 2x is not available with your hardware and k3b, and it therefore goes back to full speed.

---

### Post by goldshirt9 on 2011-07-09
poor quality dvd's maybe.
burning at 2x shouldn't be a problem.
what are the disc's 
dvd+ or dvd- and i assume the burner can accommodate both types
.have you tried make  variety of disc

---

### Post by Rayaz on 2011-07-09
Use GnomeBaker, Brasero ruined so many DVDs for me:(

---

### Post by ajgreeny on 2011-07-09
The OP was using k3b, probably the best burner there is for Linux!

---

### Post by andrew.46 on 2011-07-09
You seem to be using Jörg Schilling's cdrecord rather than the Debian fork, unless I am terribly mistaken. Which version of Ubuntu are you using? Perhaps if you are burning an iso to dvd you could try growisofs instead:

```
growisofs -dvd-compat -Z /dev/dvd=**[COLOR="Red"]my_file.iso[/COLOR]**
```

changing the path and name for your own file of course...

---

### Post by Ratnip on 2011-07-09
> **ajgreeny said:**
> I have no idea whether it will help, but it is worth trying a burn at as slow a speed as you can rather than the high speed you used that time.

Apologies if that does not help.
I am new to Linux and Ubuntu.  I tried to burn an .iso image on Brasero. After I tried, and it failed, I cannot remove that from the Barerso directory.  To make matters worse, I cannot burn anything now.
Please help.
Ron

---

### Post by ajgreeny on 2011-07-10
Delete the hidden folders in your home:-
/home/*user*/.gconf/apps/brasero
/home/*user*/.config/brasero
and see if that helps.

Hit Ctrl+H to show hidden files and folders in nautilus.

---

### Post by MSetty on 2011-07-10
> **andrew.46 said:**
> You seem to be using Jörg Schilling's cdrecord rather than the Debian fork, unless I am terribly mistaken. Which version of Ubuntu are you using? Perhaps if you are burning an iso to dvd you could try growisofs instead:

```
growisofs -dvd-compat -Z /dev/dvd=**[COLOR="Red"]my_file.iso[/COLOR]**
```

changing the path and name for your own file of course...

I'm using Maverick. I tried growisofs. It threw an input/output error.```
:-? the LUN appears to be stuck writing LBA=310h, keep retrying in 283ms
    1605632/2624086016 ( 0.1%) @0.0x, remaining 1524:24 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=310h failed with SK=4h/ASC=44h/ACQ=D9h]: Input/output error
:-( write failed: Input/output error
/dev/dvd: flushing cache
/dev/dvd: updating RMA
/dev/dvd: closing disc
/dev/dvd: reloading tray

```
 
It's a memorex dvd-rw. I literally used the same type the night before it started failing, and it worked like a charm. I tried using Brasero, k3b, growisofs.

---

### Post by MSetty on 2011-07-10
bump

---

