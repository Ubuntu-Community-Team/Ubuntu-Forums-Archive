---
title: "k3b doesn't want to burn audio CD - already have mp3 fix"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by 2dfighter on 2007-06-29
I am relatively new to the Ubuntu community, but I do have a little experience with what I'm doing. I'm not an ace of console commands, but I get the general idea of how linux works. Now, onto my problem:

I have recently installed 7.04, coming back from Windows. I installed Eft, and then updated to Fawn, and then downloaded and made a copy of Fawn. I burnt the ISO using k3b, everything went fine. Now that I'm trying to make an audio CD, it told me to get the mp3 support. I've done that, and now it won't work. I've tried gnomebaker as well, seems to be the same problem. The problem is, the error tells me to try TAO, and then when I do, it tells me to try DOA, which is what I used to begin with. It's just one big mess.

I've included screen shots and the errors rather than explaining it further.

[http://img.photobucket.com/albums/v601/2dFighter/Screenshot.png](http://img.photobucket.com/albums/v601/2dFighter/Screenshot.png)

```
]System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
SONY DVD RW AW-Q170A 1.70 (/dev/hdc, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite, Layer Jump]

TOSHIBA DVD-ROM SD-M1612 1808 (/dev/hdd, ) [CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM] [None]
Used versions
-----------------------
cdrecord: 1.1.2

cdrecord
-----------------------
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
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identification : 'DVD RW AW-Q170A '
Revision       : '1.70'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 890880 = 870 KB
FIFO size      : 12582912 = 12288 KB
Track 01: audio   26 MB (02:36.12) no preemp swab     
Track 02: audio   27 MB (02:45.02) no preemp swab     
Track 03: audio   23 MB (02:22.06) no preemp swab     
Track 04: audio   25 MB (02:32.50) no preemp swab     
Track 05: audio   29 MB (02:54.26) no preemp swab     
Track 06: audio   36 MB (03:38.02) no preemp swab     
Track 07: audio   19 MB (01:53.53) no preemp swab     
Track 08: audio   37 MB (03:45.18) no preemp swab     
Track 09: audio   39 MB (03:52.54) no preemp swab     
Track 10: audio   37 MB (03:40.58) no preemp swab     
Track 11: audio   19 MB (01:58.65) no preemp swab     
Track 12: audio   19 MB (01:58.32) no preemp swab     
Track 13: audio   35 MB (03:30.81) no preemp swab     
Track 14: audio   19 MB (01:55.68) no preemp swab     
Track 15: audio   38 MB (03:50.50) no preemp swab     
Track 16: audio   23 MB (02:18.48) no preemp swab     
Track 17: audio   31 MB (03:04.53) no preemp swab     
Track 18: audio   32 MB (03:14.12) no preemp swab     
Speed set to 4234 KB/s
Track 19: audio   22 MB (02:16.29) no preemp swab     
Track 20: audio   14 MB (01:23.98) no preemp swab     
Track 21: audio   28 MB (02:47.32) no preemp swab     
Track 22: audio   28 MB (02:48.41) no preemp swab     
Track 23: audio   32 MB (03:11.06) no preemp swab     
Track 24: audio   27 MB (02:44.32) no preemp swab     
Track 25: audio   44 MB (04:25.36) no preemp swab     
Track 26: audio   27 MB (02:44.02) no preemp swab     
Track 27: audio   32 MB (03:16.10) no preemp swab     
Total size:      790 MB (78:19.86) = 352490 sectors
Lout start:      790 MB (78:21/65) = 352490 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11834 (97:24/16)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 24
Manufacturer: SONY Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 7359
Starting to write CD/DVD at speed  24.0 in real force TAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of   26 MB written.
Errno: 0 (Success), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63504
cmd finished after 0.014s timeout 40s
/usr/bin/X11/wodim: A write error occured.
/usr/bin/X11/wodim: Please properly read the error message above.
Errno: 0 (Success), flush cache scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 03 00 00 01 2F 0A 00 00 00 00 0C 07 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x07 (write error - recovery needed) Fru 0x0
Sense flags: Blk 303 (valid) 
cmd finished after 1.386s timeout 120s
write track data: error after 0 bytes
Trouble flushing the cache
Writing  time:   12.057s
Average write speed 708.0x.
Fixating...
Errno: 0 (Success), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 72 04 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x72 Qual 0x04 (empty or partially written reserved track) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 480s
cmd finished after 0.002s timeout 480s
/usr/bin/X11/wodim: Cannot fixate disk.
Fixating time:    0.004s
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/X11/wodim -v gracetime=2 dev=/dev/hdc speed=24 -tao driveropts=burnfree -force -useinfo -audio /tmp/kde-moses/k3b_audio_0_01.inf /tmp/kde-moses/k3b_audio_0_02.inf /tmp/kde-moses/k3b_audio_0_03.inf /tmp/kde-moses/k3b_audio_0_04.inf /tmp/kde-moses/k3b_audio_0_05.inf /tmp/kde-moses/k3b_audio_0_06.inf /tmp/kde-moses/k3b_audio_0_07.inf /tmp/kde-moses/k3b_audio_0_08.inf /tmp/kde-moses/k3b_audio_0_09.inf /tmp/kde-moses/k3b_audio_0_10.inf /tmp/kde-moses/k3b_audio_0_11.inf /tmp/kde-moses/k3b_audio_0_12.inf /tmp/kde-moses/k3b_audio_0_13.inf /tmp/kde-moses/k3b_audio_0_14.inf /tmp/kde-moses/k3b_audio_0_15.inf /tmp/kde-moses/k3b_audio_0_16.inf /tmp/kde-moses/k3b_audio_0_17.inf /tmp/kde-moses/k3b_audio_0_18.inf /tmp/kde-moses/k3b_audio_0_19.inf /tmp/kde-moses/k3b_audio_0_20.inf /tmp/kde-moses/k3b_audio_0_21.inf /tmp/kde-moses/k3b_audio_0_22.inf /tmp/kde-moses/k3b_audio_0_23.inf /tmp/kde-moses/k3b_audio_0_24.inf /tmp/kde-moses/k3b_audio_0_25.inf /tmp/kde-moses/k3b_audio_0_26.inf /tmp/kde-moses/k3b_audio_0_27.inf 

```

---

### Post by 2dfighter on 2007-06-29
[http://img.photobucket.com/albums/v601/2dFighter/Screenshot-2.png](http://img.photobucket.com/albums/v601/2dFighter/Screenshot-2.png)

```
System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
SONY DVD RW AW-Q170A 1.70 (/dev/hdc, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite, Layer Jump]

TOSHIBA DVD-ROM SD-M1612 1808 (/dev/hdd, ) [CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM] [None]
Used versions
-----------------------
cdrecord: 1.1.2

cdrecord
-----------------------
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
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identification : 'DVD RW AW-Q170A '
Revision       : '1.70'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 890880 = 870 KB
FIFO size      : 12582912 = 12288 KB
Encoding speed : 394x (29495 sectors/s) for libedc from Heiko Eißfeldt
Track 01: audio   26 MB (02:36.12) no preemp swab     
Track 02: audio   27 MB (02:45.02) no preemp swab     
Track 03: audio   23 MB (02:22.06) no preemp swab     
Track 04: audio   25 MB (02:32.50) no preemp swab     
Track 05: audio   29 MB (02:54.26) no preemp swab     
Track 06: audio   36 MB (03:38.02) no preemp swab     
Track 07: audio   19 MB (01:53.53) no preemp swab     
Track 08: audio   37 MB (03:45.18) no preemp swab     
Track 09: audio   39 MB (03:52.54) no preemp swab     
Track 10: audio   37 MB (03:40.58) no preemp swab     
Track 11: audio   19 MB (01:58.65) no preemp swab     
Track 12: audio   19 MB (01:58.32) no preemp swab     
Track 13: audio   35 MB (03:30.81) no preemp swab     
Track 14: audio   19 MB (01:55.68) no preemp swab     
Track 15: audio   38 MB (03:50.50) no preemp swab     
Track 16: audio   23 MB (02:18.48) no preemp swab     
Track 17: audio   31 MB (03:04.53) no preemp swab     
Track 18: audio   32 MB (03:14.12) no preemp swab     
Speed set to 2822 KB/s
Track 19: audio   22 MB (02:16.29) no preemp swab     
Track 20: audio   14 MB (01:23.98) no preemp swab     
Track 21: audio   28 MB (02:47.32) no preemp swab     
Track 22: audio   28 MB (02:48.41) no preemp swab     
Track 23: audio   32 MB (03:11.06) no preemp swab     
Track 24: audio   27 MB (02:44.32) no preemp swab     
Track 25: audio   44 MB (04:25.36) no preemp swab     
Track 26: audio   27 MB (02:44.02) no preemp swab     
Track 27: audio   32 MB (03:16.10) no preemp swab     
Total size:      781 MB (77:27.86) = 348590 sectors
Lout start:      782 MB (77:29/65) = 348590 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11834 (97:24/16)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 24
Manufacturer: SONY Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 11259
Starting to write CD/DVD at speed  16.0 in real force RAW/RAW96R mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
/usr/bin/X11/wodim: WARNING: Drive returns wrong startsec (0) using -11834 from ATIP
Writing lead-in at sector -11834
Lead-in write time:   15.542s
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of   27 MB written.
Errno: 0 (Success), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1A 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63648
cmd finished after 0.005s timeout 40s
/usr/bin/X11/wodim: A write error occured.
/usr/bin/X11/wodim: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:   20.687s
Average write speed 904.9x.
Writing Leadout...
Errno: 0 (Success), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 05 51 AE 00 00 1A 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63648
cmd finished after 0.004s timeout 40s
write leadout data: error after 0 bytes
Fixating...
Errno: 0 (Success), flush cache scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 03 FF FF FF FA 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk -6 (valid) 
cmd finished after 3.997s timeout 120s
Trouble flushing the cache
Fixating time:    4.007s
/usr/bin/X11/wodim: Drive needs to reload the media to return to proper status.
BURN-Free was 1 times used.

cdrecord command:
-----------------------
/usr/bin/X11/wodim -v gracetime=2 dev=/dev/hdc speed=16 -raw96r driveropts=burnfree -force -useinfo -audio /tmp/kde-moses/k3b_audio_0_01.inf /tmp/kde-moses/k3b_audio_0_02.inf /tmp/kde-moses/k3b_audio_0_03.inf /tmp/kde-moses/k3b_audio_0_04.inf /tmp/kde-moses/k3b_audio_0_05.inf /tmp/kde-moses/k3b_audio_0_06.inf /tmp/kde-moses/k3b_audio_0_07.inf /tmp/kde-moses/k3b_audio_0_08.inf /tmp/kde-moses/k3b_audio_0_09.inf /tmp/kde-moses/k3b_audio_0_10.inf /tmp/kde-moses/k3b_audio_0_11.inf /tmp/kde-moses/k3b_audio_0_12.inf /tmp/kde-moses/k3b_audio_0_13.inf /tmp/kde-moses/k3b_audio_0_14.inf /tmp/kde-moses/k3b_audio_0_15.inf /tmp/kde-moses/k3b_audio_0_16.inf /tmp/kde-moses/k3b_audio_0_17.inf /tmp/kde-moses/k3b_audio_0_18.inf /tmp/kde-moses/k3b_audio_0_19.inf /tmp/kde-moses/k3b_audio_0_20.inf /tmp/kde-moses/k3b_audio_0_21.inf /tmp/kde-moses/k3b_audio_0_22.inf /tmp/kde-moses/k3b_audio_0_23.inf /tmp/kde-moses/k3b_audio_0_24.inf /tmp/kde-moses/k3b_audio_0_25.inf /tmp/kde-moses/k3b_audio_0_26.inf /tmp/kde-moses/k3b_audio_0_27.inf 

```

---

### Post by 2dfighter on 2007-06-29
[http://img.photobucket.com/albums/v601/2dFighter/Screenshot-1.png](http://img.photobucket.com/albums/v601/2dFighter/Screenshot-1.png)

```
System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
SONY DVD RW AW-Q170A 1.70 (/dev/hdc, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite, Layer Jump]

TOSHIBA DVD-ROM SD-M1612 1808 (/dev/hdd, ) [CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM] [None]
Used versions
-----------------------
cdrecord: 1.1.2

cdrecord
-----------------------
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
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identification : 'DVD RW AW-Q170A '
Revision       : '1.70'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 890880 = 870 KB
FIFO size      : 12582912 = 12288 KB
Track 01: audio   26 MB (02:36.12) no preemp swab     
Track 02: audio   27 MB (02:45.02) no preemp swab     
Track 03: audio   23 MB (02:22.06) no preemp swab     
Track 04: audio   25 MB (02:32.50) no preemp swab     
Track 05: audio   29 MB (02:54.26) no preemp swab     
Track 06: audio   36 MB (03:38.02) no preemp swab     
Track 07: audio   19 MB (01:53.53) no preemp swab     
Track 08: audio   37 MB (03:45.18) no preemp swab     
Track 09: audio   39 MB (03:52.54) no preemp swab     
Track 10: audio   37 MB (03:40.58) no preemp swab     
Track 11: audio   19 MB (01:58.65) no preemp swab     
Track 12: audio   19 MB (01:58.32) no preemp swab     
Track 13: audio   35 MB (03:30.81) no preemp swab     
Track 14: audio   19 MB (01:55.68) no preemp swab     
Track 15: audio   38 MB (03:50.50) no preemp swab     
Track 16: audio   23 MB (02:18.48) no preemp swab     
Track 17: audio   31 MB (03:04.53) no preemp swab     
Track 18: audio   32 MB (03:14.12) no preemp swab     
Speed set to 1411 KB/s
Track 19: audio   22 MB (02:16.29) no preemp swab     
Track 20: audio   14 MB (01:23.98) no preemp swab     
Track 21: audio   28 MB (02:47.32) no preemp swab     
Track 22: audio   28 MB (02:48.41) no preemp swab     
Track 23: audio   32 MB (03:11.06) no preemp swab     
Track 24: audio   27 MB (02:44.32) no preemp swab     
Track 25: audio   44 MB (04:25.36) no preemp swab     
Track 26: audio   27 MB (02:44.02) no preemp swab     
Track 27: audio   32 MB (03:16.10) no preemp swab     
Total size:      781 MB (77:27.86) = 348590 sectors
Lout start:      782 MB (77:29/65) = 348590 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11834 (97:24/16)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 24
Manufacturer: SONY Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 11259
Starting to write CD/DVD at speed   8.0 in real force SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
/usr/bin/X11/wodim: CUE sheet not accepted. Retrying with minimum pregapsize = 1.
Errno: 0 (Success), send_cue_sheet scsi sendcmd: no error
CDB:  5D 00 00 00 00 00 00 01 C0 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 448
cmd finished after 0.000s timeout 200s
/usr/bin/X11/wodim: CUE sheet still not accepted. Please try to write in RAW (-raw96r) mode.
/usr/bin/X11/wodim: Cannot send CUE sheet.
/usr/bin/X11/wodim: Could not write Lead-in.
Writing  time:    6.173s
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/X11/wodim -v gracetime=2 dev=/dev/hdc speed=8 -dao driveropts=burnfree -force -useinfo -audio /tmp/kde-moses/k3b_audio_0_01.inf /tmp/kde-moses/k3b_audio_0_02.inf /tmp/kde-moses/k3b_audio_0_03.inf /tmp/kde-moses/k3b_audio_0_04.inf /tmp/kde-moses/k3b_audio_0_05.inf /tmp/kde-moses/k3b_audio_0_06.inf /tmp/kde-moses/k3b_audio_0_07.inf /tmp/kde-moses/k3b_audio_0_08.inf /tmp/kde-moses/k3b_audio_0_09.inf /tmp/kde-moses/k3b_audio_0_10.inf /tmp/kde-moses/k3b_audio_0_11.inf /tmp/kde-moses/k3b_audio_0_12.inf /tmp/kde-moses/k3b_audio_0_13.inf /tmp/kde-moses/k3b_audio_0_14.inf /tmp/kde-moses/k3b_audio_0_15.inf /tmp/kde-moses/k3b_audio_0_16.inf /tmp/kde-moses/k3b_audio_0_17.inf /tmp/kde-moses/k3b_audio_0_18.inf /tmp/kde-moses/k3b_audio_0_19.inf /tmp/kde-moses/k3b_audio_0_20.inf /tmp/kde-moses/k3b_audio_0_21.inf /tmp/kde-moses/k3b_audio_0_22.inf /tmp/kde-moses/k3b_audio_0_23.inf /tmp/kde-moses/k3b_audio_0_24.inf /tmp/kde-moses/k3b_audio_0_25.inf /tmp/kde-moses/k3b_audio_0_26.inf /tmp/kde-moses/k3b_audio_0_27.inf 

```

---

### Post by IanW on 2007-06-29
K3b is now at version 1.0.2. This _may_ fix your problem. Get it from [http://www.getdeb.net/]("http://www.getdeb.net/")

---

### Post by 2dfighter on 2007-06-29
Alright, I updated, and it worked... sorta. It got to 78% and then said "error 254." I then looked up the answer, and can't find one that works. Can anyone point me in the right direction this time?

---

### Post by kingofpain on 2007-08-31
Hey!
On what kind of IDE cable do you have your CDRW / DVDRW mounted? Is it an ATA33 cable?

---

### Post by wolfen69 on 2007-08-31
did you install libk3b2-mp3? THAT is what is required to burn audio cd's. it's in synaptic.

---

### Post by Jose Catre-Vandis on 2008-06-13
> **wolfen69 said:**
> did you install libk3b2-mp3? THAT is what is required to burn audio cd's. it's in synaptic.

Thanks

On Hardy you need libk3b2-extracodecs to burn cue/mp3 files :)

---

