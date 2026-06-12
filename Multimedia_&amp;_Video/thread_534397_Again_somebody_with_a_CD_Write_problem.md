---
title: "Again somebody with a CD Write problem"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by NatalieG on 2007-08-25
Hi All

When trying to burn a CD, the program terminates after a couple of tracks (see below). I tried GnomeBaker, Serpentine and also the default ISO burner.

This is the log I got for durbing an audio cd with 25 tracks. As you can see it stops after track 4 right after fixating. i know the burner works because it does work in M$. Anybody got a clue? I haven't been able to find it in the forum (or the net)

> wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '1,1,0'
scsibus: 1 target: 1 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-108 '
Revision       : '1.14'
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
Drive buf size : 1267712 = 1238 KB
FIFO size      : 12582912 = 12288 KB
 Speed set to 705 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Starting new track at sector: 11151
Starting new track at sector: 22606
Starting new track at sector: 37527
Writing  time:  177.238s
Average write speed  24.5x.
Min drive buffer fill was 81%
Fixating...
Errno: 5 (Input/output error), read track info scsi sendcmd: no error
CDB:  52 01 00 00 00 FF 00 00 1C 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 28
cmd finished after 0.509s timeout 240s
wodim: Cannot get next writable address for 'invisible' track.
wodim: This means that we are checking recorded media.
wodim: This media cannot be written in streaming mode anymore.
wodim: If you like to write to 'preformatted' RW media, try to blank the media first.
wodim: Cannot get next writable address.
Fixating time:   68.305s


---

### Post by NatalieG on 2007-08-27
I upgraded the firmware to the lastest (1.20) and force the soa write mode and now it works :confused:

---

