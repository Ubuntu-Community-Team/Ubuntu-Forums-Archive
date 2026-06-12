---
title: "Can't Burn CDs Any More"
date: 2012-08-03
forum: Multimedia Software
---

### Post by SillySod on 2012-08-03
I'm not sure what has happened lately, but I can't burn CDs any more.  I've tried with write-once discs (which have to be thrown away after the "burn failure" because they can't be used again) as well as RW ones, but each time it doesn't work.

I've tried Brasero and Gnomebaker, and here is the output from the latest attempt to record some MP3 files to an audio CD:

```
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'FREECOM_'
Identification : 'DVD+/-RW16N9    '
Revision       : 'FR11'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A (CD-RW)
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0009 (CD-R) 
Profile: 0x000A (CD-RW) (current)
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) 
Profile: 0x002B (DVD+R/DL) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
Drive buf size : 1451664 = 1417 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 706 KB/s
l write in    5 seconds.   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 35 AF 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 02 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x02 (end-of-partition/medium detected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 50.515s timeout 40s
wodim: A write error occured.
wodim: Please properly read the error message above.

write track data: error after 32323536 bytes
Writing  time:  104.774s
Average write speed  10.3x.
Min drive buffer fill was 94%
Fixating...
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.003s timeout 480s
cmd finished after 0.003s timeout 480s
Fixating time:    0.007s
wodim: Cannot fixate disk.
wodim: fifo had 701 puts and 510 gets.
wodim: fifo was 0 times empty and 497 times full, min fill was 96%.
```

There's no problem with DVDs, I can write -R, +R, RW types without any trouble using exactly the same hardware and software.

Hope somebody can help!

---

### Post by SillySod on 2012-08-03
Just noticed that this thread has come up as "lubuntu" - I've no idea what that is, or how to change it!  It should be "Ubuntu"!!

---

