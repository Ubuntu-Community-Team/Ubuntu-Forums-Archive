---
title: "Can't burn cds.."
date: 2008-08-29
forum: Multimedia Software
---

### Post by crank420 on 2008-08-29
I used to be able to burn cds on the older vresions with this burner its a memorex dvdrw but everytinw i try to burn i get this error:

ystem
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
Memorex DVD+R/RW 2.4x8AA 1.27 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD+R, DVD+RW] [DVD-ROM, DVD+RW, DVD+R, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R96R]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'Memorex '
Identification : 'DVD+R/RW 2.4x8AA'
Revision       : '1.27'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009 (CD-R)
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
Drive buf size : 1310720 = 1280 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 1411 KB/s
pregap1: -1
Track 01: audio   67 MB (06:39.60) no preemp swab copy
Total size:       67 MB (06:39.60) = 29970 sectors
Lout start:       67 MB (06:41/45) = 29970 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 329876
Starting to write CD/DVD at speed   8.0 in real force SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0C 00 00 00 00 64 C0 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x64 Qual 0xC0 (illegal mode for this track) [No matching qualifier] Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 5.070s timeout 200s
/usr/bin/wodim: OPC failed.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0C 00 00 00 00 64 C0 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x64 Qual 0xC0 (illegal mode for this track) [No matching qualifier] Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 2.893s timeout 200s
Writing pregap for track 1 at -150
write track pad data: error after 0 bytes
BFree: 0 K BSize: 1470 K
Starting new track at sector: 0
Track 01:    0 of   67 MB written.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0C 00 00 00 00 64 C0 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x64 Qual 0xC0 (illegal mode for this track) [No matching qualifier] Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 3.152s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:   16.181s
Average write speed  36.2x.
Fixating...
Fixating time:    0.010s
BURN-Free was never needed.
/usr/bin/wodim: fifo had 192 puts and 1 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=8 -dao driveropts=burnfree -force -eject -useinfo -audio /tmp/kde-joseph/k3b_audio_1_01.inf 




I have searched the ewb hi and low for a fix and i can't seem to find it can someone PLEASE help...

---

### Post by crank420 on 2008-08-29
and it says the burner does not like the medium if that helps any... but i have already tryed other new discs...

---

### Post by djRobbieF on 2008-08-29
IMO, your problem is likely going to be (in no particular order):
1) You're burning at too high a speed, try using the slowest speed available.
2) What you're trying to burn can't buffer in a speed fast enough for the burn operation; try placing it in an ISO first and then burning.
3) Your drive's firmware is bad, either update it or replace the drive.
4) Your disks are bad.
5) The source files are bad; try burning a different file and see if you get the same error.

---

