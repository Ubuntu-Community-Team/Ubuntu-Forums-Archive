---
title: "gnomebaker or k3b burn errors, cant figure out why"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by sdowney717 on 2007-04-10
I am trying to burn an iso
both programs will fail to complete the burn
any ideas?

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'SAMSUNG '
Identification : 'CD-R/RW SW-224B '
Revision       : 'R201'
Device seems to be: Generic mmc CD-RW.
Current: 0x000A (CD-RW)
Profile: 0x000A (CD-RW) (current)
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1973664 = 1927 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 706 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 02 4A 56 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 71 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.012s timeout 40s
wodim: A write error occured.
wodim: Please properly read the error message above.

write track data: error after 307408896 bytes
Writing  time:  515.999s
Average write speed   9.5x.
Min drive buffer fill was 100%
Fixating...
Fixating time:   85.779s
BURN-Free was never needed.

---

### Post by chaumurky on 2007-05-16
Hmm, same here:

```

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '4,0,0'
scsibus: 4 target: 0 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-4084N'
Revision       : 'KQ09'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 9268 kB/s 52x CD 6x DVD
FIFO size      : 12582912 = 12288 KB
Speed set to 2822 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Starting new track at sector: 0
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 02 2E 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 30 02 80 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.002s timeout 40s
wodim: The current problem looks like a buffer underrun.
wodim: It looks like 'driveropts=burnfree' does not work for this drive.
wodim: Please report.
wodim: Make sure that you are root, enable DMA and check your HW/OS set up.

write track data: error after 1142784 bytes
Writing  time:   12.100s
Average write speed 204.9x.
Min drive buffer fill was 98%
Fixating...
WARNING: Some drives don't like fixation in dummy mode.
Fixating time:   28.572s

```

```

ls -l /media
total 24
lrwxrwxrwx 1 root      root    6 2007-05-04 03:10 cdrom -> cdrom0
drwxrwxrwx 2 root      root 4096 2007-05-04 03:10 cdrom0
drwxr-xr-x 3 root      root 4096 2007-05-16 22:05 gutsy

```

HP DV6000 notebook

---

### Post by albatroz2k on 2007-05-26
Could you solve your info? 
Which version of Ubuntu are you using?

I have an HP Pavilion dv6000 and have problems burning CDs 
with Ubuntu Feisty Fawn (7.04)

---

### Post by vayde on 2007-05-31
Same error for me as chaumurky.  Fresh install of Feisty on a brand new XPS m1210.

---

