---
title: "Ubuntu 11.10 - K3b Not Completing Burn Successfully"
date: 2011-12-14
forum: Multimedia Software
---

### Post by fleamour on 2011-12-14
K3b will not complete burning of .iso successfully.  I only have two types of branded RW media, both fail.  The following was using an ASDA (UK, Walmart owned) DVD RW.  The disk can apparently just be overwritten each time.  Forcing format did not help.  I do not recall problems in 11.04.  Can anyone decipher following error report?: 

```
  Devices
-----------------------
PIONEER DVD-RW  DVR-115D 1.06 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

System
-----------------------
K3b Version: 2.0.2
KDE Version: 4.7.2 (4.7.2)
QT Version:  4.7.4
Kernel:      3.0.0-14-generic

Used versions
-----------------------
cdrecord: 1.1.11

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.11
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-115D'
Revision       : '1.06'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0013 (DVD-RW restricted overwrite)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) (current)
Profile: 0x0013 (DVD-RW restricted overwrite) (current)
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1605632 = 1568 KB
FIFO size      : 12582912 = 12288 KB
Errno: 5 (Input/output error), read track info scsi sendcmd: no error
CDB:  52 00 00 00 00 00 00 00 1C 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.006s timeout 240s
/usr/bin/wodim: WARNING: Data may not fit on standard 74min disk.
Speed set to 5540 KB/s
Track 01: data   677 MB        
Total size:      777 MB (77:03.65) = 346774 sectors
Lout start:      778 MB (77:05/49) = 346774 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Starting to write CD/DVD at speed   4.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... Errno: 5 (Input/output error), reserve track scsi sendcmd: no error
CDB:  53 00 00 00 00 00 05 4A 96 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 72 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x72 Qual 0x05 (no more track reservations allowed) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.005s timeout 200s
/usr/bin/wodim: Cannot open new session.
input buffer ready.
Writing  time:    0.110s
/usr/bin/wodim: fifo had 192 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=4 -sao driveropts=burnfree -overburn -data -tsize=346774s -
```

---

### Post by wolfen69 on 2011-12-14
See [this]("https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/149076/comments/57") and follow up comments.

---

### Post by fleamour on 2011-12-15
A four year old bug in wodim?  The joys of Linux I guess.  Wish there was an easy fix...

---

### Post by wolfen69 on 2011-12-15
Btw, what speed were you trying to burn at?

---

### Post by fleamour on 2011-12-15
Auto, though I did try lower settings.

---

### Post by bluexrider on 2011-12-15
wodim is refusing to do the job because it needs permission to set  memory limits. To do this, you either run wodim as root or set the SUID  bit for /usr/bin/wodim and introduce potential security risks, OR...
Add this line to /etc/security/limits.conf:
 @cdrom     -     memlock     unlimited
 Just make sure you are part of the 'cdrom' group.

shouldn't be to hard to fix

---

### Post by fleamour on 2011-12-15
I did add the text line:

@cdrom - memlock unlimited

to

sudo gedit /etc/security/limits.conf

But it made no difference.  Although I am not sure how to be a member of the "cdrom" group?

I am also not sure how to run as root or set the SUID bit.  Maybe a Google will help.  (I am just popping out for coffee...)

---

### Post by fleamour on 2011-12-15
Woah!!!

Some hardcore Googling revealed a German forum:

[http://forum.ubuntuusers.de/topic/kleines-projekt-mit-paketverwaltung-die-schil/6/#post-2584797](http://forum.ubuntuusers.de/topic/kleines-projekt-mit-paketverwaltung-die-schil/6/#post-2584797)

The gist of which being:

Strange packets can compromise the system, nuclear reactors can melt the butter and make sour milk! 
Please only install if you know what you are doing!

```
wget http://media.ubuntuusers.de/forum/attachments/2584797/cdrtools-3.0%7Eantiqua0_i386.tar.bz2
tar -xvjf cdrtools-3.0~antiqua0_i386.tar.bz2
cd cdrtools-3.0~antiqua0_i386    
sudo ./install_cdrtools install
```

Deinstallation:

```
cd cdrtools-3.0~antiqua0_i386 
sudo ./install_cdrtools purge
```

Turns out media was faulty all along!  But can now reliably reproduce .iso burn on good media.


\\:D/ :biggrin: :grin:

---

### Post by fleamour on 2011-12-15
Ugh!

After all that!  Was faulty media all along, well that's one way to waste an afternoon.

Works with ***both*** cdrkit & cdrtools.  Still my Google skillz were considerably sharpened.  Hopefully it'll help some poor soul.  Lesson learned: Never overlook the obvious...

---

### Post by bluexrider on 2011-12-15
> **fleamour said:**
> Ugh!

After all that!  Was faulty media all along, well that's one way to waste an afternoon.

Works with ***both*** cdrkit & cdrtools.  Still my Google skillz were considerably sharpened.  Hopefully it'll help some poor soul.  Lesson learned: Never overlook the obvious...
OMG! don't ya hate that when it happens?

I got more friggin coasters using Memorex than anything else. Do what I do, skeet shooter....

Glad you got it going.

mark this one

(SOLVED)

---

### Post by digital_k on 2011-12-16
I've encountered this issue in both kb3 and also Brasero. Upon searching, I found that disabling the md5 plugin puts an end to coaster making.

---

