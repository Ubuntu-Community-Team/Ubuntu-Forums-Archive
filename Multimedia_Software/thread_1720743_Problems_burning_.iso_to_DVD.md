---
title: "Problems burning .iso to DVD"
date: 2011-04-03
forum: Multimedia Software
---

### Post by vrijstijler on 2011-04-03
Today I want to install Ubuntu on a friends laptop. I finally convinced him to leave Windows and move on to Ubuntu.

Ironically this has brought me into problems. I have downloaded the 
ubuntu-10.10-dvd-i386.iso and ubuntu-10.10-desktop-i386.iso to make a bootable cd/dvd to install Ubuntu.

Now both K3b and Brasero give me problems burning one of the .iso files. I already waste some CDr and DVDr. Please help.

I will share some logfiles for your info;

1. From K3b
--------------
Devices
-----------------------
MATSHITA DVD-RAM UJ870QJ 1.00 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, Restricted Overwrite, Layer Jump] [%7]

System
-----------------------
K3b Version: 2.0.1
KDE Version: 4.5.1 (KDE 4.5.1)
QT Version:  4.7.0
Kernel:      2.6.35-28-generic

Used versions
-----------------------
cdrecord: 1.1.10
.....
.....
Track 01:  131 of 4156 MB written (fifo 100%) [buf  99%]   3.8x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 01 06 2B 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F1 00 04 00 01 03 40 0A 00 29 00 00 03 00 00 00
Sense Key: 0x4 Hardware Error, deferred error, Segment 0
Sense Code: 0x03 Qual 0x00 (peripheral device write fault) Fru 0x0
Sense flags: Blk 66368 (valid) 
cmd finished after 4.112s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 137451520 bytes
Writing  time:   58.823s
Average write speed  73.2x.
Min drive buffer fill was 93%
Fixating...
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 72 04 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x72 Qual 0x04 (empty or partially written reserved track) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.003s timeout 1000s
Fixating time:    0.005s
/usr/bin/wodim: fifo had 2357 puts and 2166 gets.
/usr/bin/wodim: fifo was 0 times empty and 1224 times full, min fill was 87%.
--------------

2. From Brasero
--------------
BraseroLibburn SCSI error condition on command 2Ah WRITE(10): See MMC specs: Sense Key 4 "Drive error", ASC 03 ASCQ 00
BraseroLibburn Something went wrong
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
	error		= 15
	message	= "An error occurred while writing to disc"
BraseroLibburn stopping
Session error : An error occurred while writing to disc (brasero_burn_record brasero-burn.c:2862)
--------------

3. Using Wodim in terminal;
--------------
cmd finished after 5.330s timeout 40s

write track data: error after 3110912 bytes
wodim: A write error occured.
wodim: Please properly read the error message above.
Writing  time:   25.109s
Average write speed 111.0x.
Min drive buffer fill was 93%
Fixating...
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 72 04 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x72 Qual 0x04 (empty or partially written reserved track) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 1000s
Fixating time:    0.005s
wodim: fifo had 241 puts and 50 gets.
wodim: fifo was 0 times empty and 17 times full, min fill was 93%.
-----------------

---

### Post by wolfen69 on 2011-04-03
It says it burned at 72x. I'm not sure that is accurate, but try again at a slow speed such as 8x.

---

### Post by ghostborg on 2011-04-03
If you downloaded a cd image then use a CD and a DVD disc if you have a DVD image.

I've used K3b Burn Image.
Next to the Burn Medium I choose a speed for the disc.
That depends on the speed of your writer and the disc used.
I choose 24x for mine even though the CD disc is 52x and the writer is I think 48x for CD's .
For the writing app I choose growiso for burning iso images.
and the writing mode I leave at auto.

---

### Post by andrew.46 on 2011-04-03
Perhaps try this for the dvd:

```
growisofs -dvd-compat -Z /dev/dvd=ubuntu-10.10-dvd-i386.iso
```

Andrew

---

