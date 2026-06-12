---
title: "Having Issues using any burning program as well as 4L lightscribe util"
date: 2008-09-21
forum: Multimedia Software
---

### Post by Ruffah-Ras on 2008-09-21
Ok, I just recently switched from Slackware 12.1 to Ubuntu Studio (the low latency kernel is what got me to switch), but I had lightscribe (4L) working in slackware as well as the ability to burn whatever without any issues...now 4L says that I need to insert a lightscribeable CD (Yes, I've tried ALL of them as well as a different brand) and I get the following error (with all burning programs even if I sudo -commandforprogram-):

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-rt
Devices
-----------------------
HL-DT-ST DVD-RW GSA-H60L DC08 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Text len: 990
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVD-RW GSA-H60L '
Revision       : 'DC08'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0000 (Reserved/Unknown)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) 
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 18223 kB/s 103x CD 13x DVD
FIFO size      : 12582912 = 12288 KB
Errno: 5 (Input/output error), start/stop unit scsi sendcmd: no error
CDB:  1B 00 00 00 01 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A 05 00 03 FF B5 80 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0xB5 Qual 0x80 (vendor unique sense code 0xB5) [No matching qualifier] Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 6.563s timeout 200s
Errno: 5 (Input/output error), start/stop unit scsi sendcmd: no error
CDB:  1B 00 00 00 01 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A 05 00 03 FF B5 80 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0xB5 Qual 0x80 (vendor unique sense code 0xB5) [No matching qualifier] Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 6.545s timeout 200s
/usr/bin/wodim: ERROR: Could not manage to find medium size, and more than 8.0 GB of data.
/usr/bin/wodim: Cannot write more than remaining DVD capacity.
pregap1: -1
Track 01: audio   50 MB (04:58.50) no preemp swab copy
Track 02: audio   34 MB (03:24.76) no preemp swab copy
Track 03: audio   34 MB (03:27.62) no preemp swab copy
Track 04: audio   35 MB (03:29.34) no preemp swab copy
Track 05: audio   44 MB (04:25.61) no preemp swab copy
Track 06: audio   39 MB (03:53.80) no preemp swab copy
Track 07: audio   46 MB (04:34.24) no preemp swab copy
Track 08: audio   39 MB (03:53.64) no preemp swab copy
Track 09: audio   39 MB (03:52.57) no preemp swab copy
Track 10: audio   43 MB (04:20.84) no preemp swab copy
Track 11: audio   34 MB (03:25.36) no preemp swab copy
Track 12: audio   39 MB (03:54.32) no preemp swab copy
Total size:      481 MB (47:40.62) = 214547 sectors
Lout start:      481 MB (47:42/47) = 214547 sectors
Current Secsize: 2048
  ATIP start of lead in:  -150 (00:00/00)
Disk type:    unknown dye (reserved id code)
Manuf. index: -1
Manufacturer: unknown (not in table)

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=18 -dao driveropts=burnfree textfile=/tmp/k3bSgszlc.dat -eject -useinfo -audio /tmp/kde-illicit/k3b_audio_0_01.inf /tmp/kde-illicit/k3b_audio_0_02.inf /tmp/kde-illicit/k3b_audio_0_03.inf /tmp/kde-illicit/k3b_audio_0_04.inf /tmp/kde-illicit/k3b_audio_0_05.inf /tmp/kde-illicit/k3b_audio_0_06.inf /tmp/kde-illicit/k3b_audio_0_07.inf /tmp/kde-illicit/k3b_audio_0_08.inf /tmp/kde-illicit/k3b_audio_0_09.inf /tmp/kde-illicit/k3b_audio_0_10.inf /tmp/kde-illicit/k3b_audio_0_11.inf /tmp/kde-illicit/k3b_audio_0_12.inf

Anyone have any idea what to do?

---

### Post by Ruffah-Ras on 2008-09-22
Damn this got buried quick :D

---

