---
title: "DeVeDe  K3b - Problem with ISO"
date: 2010-02-19
forum: Multimedia Software
---

### Post by OCN on 2010-02-19
Used DeVeDe to take a Avi that was 700mb which is now a 2gb iso file which will open fine with VLC player with the custom menu I made and the movie plays fine but K3b will not burn the to the media and I tried several blank disk of the same media now and no luck... I don't have any other media to try but this same media worked fine with K3b before and recent so I don't know  but I never tried it using it like this before meaning with DeVeDe.

> Devices
-----------------------
HL-DT-ST DVDRAM GSA-H42L SL00 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

System
-----------------------
K3b Version: 1.68.0
KDE Version: 4.3.2 (KDE 4.3.2)
QT Version:  4.5.2
Kernel:      2.6.31-16-generic

Used versions
-----------------------
cdrecord: 1.1.9

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-H42L '
Revision       : 'SL00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x001B (DVD+R)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) (current)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) 
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1114112 = 1088 KB
Drive DMA Speed: 14304 kB/s 81x CD 10x DVD
FIFO size      : 12582912 = 12288 KB
Speed set to 22160 KB/s
Track 01: data  1999 MB        
Total size:     2295 MB (227:27.80) = 1023585 sectors
Lout start:     2296 MB (227:29/60) = 1023585 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 2295104 Blocks current: 2295104 Blocks remaining: 1271519
Starting to write CD/DVD at speed  17.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... Errno: 5 (Input/output error), reserve track scsi sendcmd: no error
CDB:  53 00 00 00 00 00 0F 9E 61 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 35 2D 03 0E 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 14.285s timeout 200s
/usr/bin/wodim: Cannot open new session.
input buffer ready.
Writing  time:   14.343s
/usr/bin/wodim: fifo had 192 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=16 -sao driveropts=burnfree -data -tsize=1023585s -


---

### Post by SuperSonic4 on 2010-02-19
You are using a blank DVD and not a CD?

---

### Post by eddietours on 2010-02-19
just incert the blank dvd right click on the image select write to disk l do it all time works

---

### Post by OCN on 2010-02-19
> **SuperSonic4 said:**
> You are using a blank DVD and not a CD?

I am using a DVD+r 16x HP

> **eddietours said:**
> just incert the blank dvd right click on the image select write to disk l do it all time works

Dude wtf!

---

### Post by OCN on 2010-02-19
bump, MOOOOOOOOOOOOOOOOOOOOOOOO, MOOOOOOOOOOOOOOOOOOOO.. ..... 

2010, IDIOCRACY is really happening :-({|=

---

### Post by andrea000 on 2010-02-19
devede makes a iso file so all you need to do is
right click it and write it to disk there is no
need to burn with k3b.2mandvd does a better job
with menu's i think but it takes it longer to make
a dvd.

---

### Post by OCN on 2010-02-19
my problem is it is failing each time I try to burn, I burned a normal data session and it worked fine so my writter is fine

---

### Post by OCN on 2010-02-19
moooooooooooooooooooooooooooooooooooooooooooooooooo 

its spreading, why so serious and why so many stuck on ubuntu.

---

### Post by eddietours on 2010-02-19
any luck?

---

