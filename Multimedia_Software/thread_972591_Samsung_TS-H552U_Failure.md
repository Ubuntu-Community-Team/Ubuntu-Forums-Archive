---
title: "Samsung TS-H552U Failure"
date: 2008-11-05
forum: Multimedia Software
---

### Post by delonix on 2008-11-05
Despite trying many things from speed to mode I create coaster.

On an otherwise functioning Soyo MoBo with the following:

cd /home/delonix/bin;cat burn 

delonix@bill:~$ cd /home/delonix/bin;cat burn
#!/bin/sh


/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=40 -tao driveropts=burnfree -eject -overburn -multi -xa -tsize=304346s -force $1

delonix@bill:~/bin$ 

This always fails, including DAO, TAO, speeds 4, 8, 16, 40, and auto on both mode and speed

Phillips and Staples 52x CD-Rs always fail (alas)

[email]root@bill:/home/iso.imag[/email]es# /home/delonix/bin/burn *.iso
TOC Type: 3 = CD-ROM XA mode 2
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
Driveropts: 'burnfree'
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identification : 'CD/DVDW TS-H552U'
Revision       : 'US03'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1968384 = 1922 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 12582912 = 12288 KB
Track 01: data   594 MB        
Total size:      682 MB (67:37.97) = 304348 sectors
Lout start:      683 MB (67:39/73) = 304348 sectors
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
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 55498
Speed set to 7056 KB/s
Starting to write CD/DVD at speed  40.0 in real force TAO mode for multi session.
Last chance to quit, starting real write i   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    1 of  594 MB written (fifo  99%) [buf  75%]   0.4x.Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 02 4D 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 71 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 2.453s timeout 40s

write track data: error after 1206272 bytes
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
Writing  time:   49.257s
Average write speed 126.7x.
Fixating...
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 72 01 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x72 Qual 0x01 (session fixation error writing lead-in) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 36.442s timeout 480s
cmd finished after 36.442s timeout 480s
/usr/bin/wodim: Cannot fixate disk.
Fixating time:   36.445s
BURN-Free was never needed.
/usr/bin/wodim: fifo had 211 puts and 20 gets.
/usr/bin/wodim: fifo was 0 times empty and 4 times full, min fill was 95%.
[email]root@bill:/home/iso.imag[/email]es# 

Please help.  It smells like a driver issue. Samsung is Windows-centric and seems to provide no help.  Other driver sources just search forever without finding a linux firmware update.

Thank you,  Bill Graham

---

### Post by silentknyght on 2008-11-16
Having similar issues burning CD-R coasters with my samsung SH-S223F dvdrw.  Burning dvds seems to be fine.  Can't find anything other than a windows executable on the Samsung page(s) to update the firmware.

---

