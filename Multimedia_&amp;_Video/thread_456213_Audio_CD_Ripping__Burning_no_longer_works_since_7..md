---
title: "Audio CD Ripping / Burning no longer works since 7.4 update"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by Shadoglare on 2007-05-27
This is a couple of the many frustrations I've had (and continue to have) after doing the update to 7.4. 

After a fair bit of work I got SoundJuicer to work to rip to mp3 back on the ole 6.10, now it doesn't work again. The option I created is there, but the sound files it creates end up being garbled junk. 

As far as burning, I've tried both k3b and Baker, both of which bomb out pretty much as soon as the burn starts. 

k3b just says there was an "unknown error" and gives up... Baker gives me this (I started doing "dummy" tests after creating four coasters in a row):

> wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'ASUS    '
Identification : 'DRW-1612BL      '
Revision       : '1.06'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1484032 = 1449 KB
FIFO size      : 12582912 = 12288 KB
hSpeed set to 8467 KB/s
ort strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 132964
Starting to write CD/DVD at speed  48.0 in dummy TAO mode for single session.
Last chance to quit, starting dummy write in 5 seconds.   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Starting new track at sector: 0
Errno: 0 (Success), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 01 0E 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63504
cmd finished after 0.000s timeout 40s
wodim: A write error occured.
wodim: Please properly read the error message above.

write track data: error after 635040 bytes
Trouble flushing the cache
Writing  time:   29.218s
Average write speed 103.6x.
Fixating...
Errno: 0 (Success), flush cache scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 71 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 20.160s timeout 120s
WARNING: Some drives don't like fixation in dummy mode.
Fixating time:    0.208s
BURN-Free was 2 times used.


The "medium error" would make me think it was a problem with the CD-R, but like I mentioned this happened several times in a row using CDs from a package that all worked fine before - that, and test-burns using data rather than audio test out OK too.

If anybody has any suggestions on where to start in getting this thing working again, I'd much appreciate it - thanks!

---

