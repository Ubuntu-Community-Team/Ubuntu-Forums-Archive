---
title: "K3b error:  Cdrecord has no permission to open the device"
date: 2008-08-08
forum: Multimedia Software
---

### Post by MikeB23930 on 2008-08-08
I am attempting to use K3b to create an audio cd from some mp3 files.  Everything seems to go well until K3b reaches the "Sending cue sheet" stage at which point it freezes and eventually displays the message

"Cdrecord has no permission to open the device"

The ouput of the K3b debug file is at the bottom of this message.  I'm runing Kubuntu 8.04.

Any help would be greatly appreciated.

Thanks,

Mike

K3b debug file:

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
AOPEN DUW1608/ARR A060 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R96R, Restricted Overwrite]

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
Text len: 216
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'AOPEN   '
Identification : 'DUW1608/ARR     '
Revision       : 'A060'
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
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
Drive buf size : 1310720 = 1280 KB
FIFO size      : 12582912 = 12288 KB
pregap1: -1
Track 01: audio   27 MB (02:46.01) no preemp swab copy
Track 02: audio   28 MB (02:48.76) no preemp swab copy
Track 03: audio   22 MB (02:13.12) no preemp swab copy
Track 04: audio   32 MB (03:15.86) no preemp swab copy
Track 05: audio   26 MB (02:38.62) no preemp swab copy
Track 06: audio   23 MB (02:20.70) no preemp swab copy
Track 07: audio   21 MB (02:06.60) no preemp swab copy
Track 08: audio   24 MB (02:26.10) no preemp swab copy
Track 09: audio   24 MB (02:26.56) no preemp swab copy
Track 10: audio   26 MB (02:38.14) no preemp swab copy
Track 11: audio   21 MB (02:07.25) no preemp swab copy
Track 12: audio   17 MB (01:46.14) no preemp swab copy
Track 13: audio   26 MB (02:36.61) no preemp swab copy
Track 14: audio   25 MB (02:33.37) no preemp swab copy
Track 15: audio   23 MB (02:18.92) no preemp swab copy
Track 16: audio   27 MB (02:45.17) no preemp swab copy
Track 17: audio   26 MB (02:38.82) no preemp swab copy
Track 18: audio   25 MB (02:29.56) no preemp swab copy
Track 19: audio   20 MB (02:00.09) no preemp swab copy
Track 20: audio   23 MB (02:19.68) no preemp swab copy
Track 21: audio   34 MB (03:23.76) no preemp swab copy
Track 22: audio   25 MB (02:31.49) no preemp swab copy
Track 23: audio   25 MB (02:33.34) no preemp swab copy
Track 24: audio   26 MB (02:35.98) no preemp swab copy
Track 25: audio   25 MB (02:31.54) no preemp swab copy
Track 26: audio   24 MB (02:28.48) no preemp swab copy
Track 27: audio   29 MB (02:52.98) no preemp swab copy
Total size:      688 MB (68:13.74) = 307031 sectors
Lout start:      689 MB (68:15/56) = 307031 sectors
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
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 52818
Speed set to 4234 KB/s
Forcespeed is OFF.
Starting to write CD/DVD at speed  24.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 FF FF D1 C6 00 02 A0 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 02 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x02 (end-of-partition/medium detected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 212.233s timeout 200s
/usr/bin/wodim: Could not write Lead-in.
Errno: 5 (Input/output error), prevent/allow medium removal scsi sendcmd: fatal error
CDB:  1E 00 00 00 00 00
cmd finished after 0.000s timeout 200s
/usr/bin/wodim: fifo had 192 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
SAO startsec: -11834
Writing lead-in...
write CD-Text data: error after 0 bytes
Writing  time:  220.741s

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=24 -dao driveropts=burnfree textfile=/tmp/k3b0VQK9b.dat -overburn -useinfo -audio /tmp/kde-mikeb/k3b_audio_0_01.inf /tmp/kde-mikeb/k3b_audio_0_02.inf /tmp/kde-mikeb/k3b_audio_0_03.inf /tmp/kde-mikeb/k3b_audio_0_04.inf /tmp/kde-mikeb/k3b_audio_0_05.inf /tmp/kde-mikeb/k3b_audio_0_06.inf /tmp/kde-mikeb/k3b_audio_0_07.inf /tmp/kde-mikeb/k3b_audio_0_08.inf /tmp/kde-mikeb/k3b_audio_0_09.inf /tmp/kde-mikeb/k3b_audio_0_10.inf /tmp/kde-mikeb/k3b_audio_0_11.inf /tmp/kde-mikeb/k3b_audio_0_12.inf /tmp/kde-mikeb/k3b_audio_0_13.inf /tmp/kde-mikeb/k3b_audio_0_14.inf /tmp/kde-mikeb/k3b_audio_0_15.inf /tmp/kde-mikeb/k3b_audio_0_16.inf /tmp/kde-mikeb/k3b_audio_0_17.inf /tmp/kde-mikeb/k3b_audio_0_18.inf /tmp/kde-mikeb/k3b_audio_0_19.inf /tmp/kde-mikeb/k3b_audio_0_20.inf /tmp/kde-mikeb/k3b_audio_0_21.inf /tmp/kde-mikeb/k3b_audio_0_22.inf /tmp/kde-mikeb/k3b_audio_0_23.inf /tmp/kde-mikeb/k3b_audio_0_24.inf /tmp/kde-mikeb/k3b_audio_0_25.inf /tmp/kde-mikeb/k3b_audio_0_26.inf /tmp/kde-mikeb/k3b_audio_0_27.inf

---

