---
title: "K3B error burning cue file (code 254)"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by Szechuan on 2007-10-18
I am trying to convert and burn a .avi file to VCD. Used DeVeDe to create a cue, and am attempting to burn using K3B, but it stops part way through and gives error code 254.

The bug output is as follows:

System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
SAMSUNG CDRW/DVD SM-308B xp01 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R16, RAW/R96R]

Used versions
-----------------------
cdrecord: 1.1.2

cdrecord
-----------------------
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'SAMSUNG '
Identification : 'CDRW/DVD SM-308B'
Revision       : 'xp01'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009 (CD-R)
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 1374208 = 1342 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 706 KB/s
Track 01: data     1 MB        
Track 02: data   429 MB        
Total size:      430 MB (42:39.58) = 191969 sectors
Lout start:      430 MB (42:41/44) = 191969 sectors
Current Secsize: 2048
  ATIP start of lead in:  -11674 (97:26/26)
  ATIP start of lead out: 359848 (79:59/73)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 23
Manufacturer: SKC Co., Ltd.
Blocks total: 359848 Blocks current: 359848 Blocks remaining: 167879
Starting to write CD/DVD at speed   4.0 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of    1 MB written.
Track 01:    1 of    1 MB written (fifo 100%) [buf  99%]   0.6x.
Track 01: Total bytes read/written: 1058400/1058400 (450 sectors).
Starting new track at sector: 450
Track 02:    0 of  429 MB written.
Track 02:    1 of  429 MB written (fifo 100%) [buf  99%]   0.2x.
Track 02:    2 of  429 MB written (fifo 100%) [buf  98%]   4.1x.
Track 02:    3 of  429 MB written (fifo 100%) [buf  98%]   4.2x.
Track 02:    4 of  429 MB written (fifo 100%) [buf  98%]   4.1x.
Track 02:    5 of  429 MB written (fifo 100%) [buf  99%]   4.3x.
Track 02:    6 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:    7 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:    8 of  429 MB written (fifo  98%) [buf  99%]   4.1x.
Track 02:    9 of  429 MB written (fifo 100%) [buf  98%]   4.2x.
Track 02:   10 of  429 MB written (fifo 100%) [buf  97%]   4.2x.
Track 02:   11 of  429 MB written (fifo  98%) [buf  99%]   4.2x.
Track 02:   12 of  429 MB written (fifo 100%) [buf  98%]   4.1x.
Track 02:   13 of  429 MB written (fifo  99%) [buf  98%]   4.2x.
Track 02:   14 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   15 of  429 MB written (fifo  99%) [buf  96%]   4.0x.
Track 02:   16 of  429 MB written (fifo 100%) [buf  98%]   4.2x.
Track 02:   17 of  429 MB written (fifo 100%) [buf  95%]   4.0x.
Track 02:   18 of  429 MB written (fifo 100%) [buf  98%]   4.2x.
Track 02:   19 of  429 MB written (fifo 100%) [buf  93%]   3.9x.
Track 02:   20 of  429 MB written (fifo 100%) [buf  99%]   4.4x.
Track 02:   21 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   22 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   23 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   24 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   25 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   26 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   27 of  429 MB written (fifo 100%) [buf  98%]   4.1x.
Track 02:   28 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   29 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   30 of  429 MB written (fifo 100%) [buf  99%]   4.0x.
Track 02:   31 of  429 MB written (fifo 100%) [buf  98%]   4.1x.
Track 02:   32 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   33 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   34 of  429 MB written (fifo 100%) [buf  98%]   3.9x.
Track 02:   35 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   36 of  429 MB written (fifo 100%) [buf  97%]   4.0x.
Track 02:   37 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   38 of  429 MB written (fifo 100%) [buf  99%]   4.0x.
Track 02:   39 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   40 of  429 MB written (fifo 100%) [buf  99%]   4.0x.
Track 02:   41 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   42 of  429 MB written (fifo  99%) [buf  99%]   4.0x.
Track 02:   43 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   44 of  429 MB written (fifo 100%) [buf  97%]   4.2x.
Track 02:   45 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   46 of  429 MB written (fifo  99%) [buf  96%]   4.0x.
Track 02:   47 of  429 MB written (fifo 100%) [buf  99%]   4.3x.
Track 02:   48 of  429 MB written (fifo 100%) [buf  95%]   4.0x.
Track 02:   49 of  429 MB written (fifo 100%) [buf  98%]   4.3x.
Track 02:   50 of  429 MB written (fifo 100%) [buf  93%]   3.9x.
Track 02:   51 of  429 MB written (fifo 100%) [buf  99%]   4.5x.
Track 02:   52 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   53 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   54 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   55 of  429 MB written (fifo 100%) [buf  98%]   4.1x.
Track 02:   56 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   57 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   58 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   59 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   60 of  429 MB written (fifo 100%) [buf  96%]   4.2x.
Track 02:   61 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   62 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   63 of  429 MB written (fifo 100%) [buf  98%]   4.0x.
Track 02:   64 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   65 of  429 MB written (fifo 100%) [buf  98%]   4.0x.
Track 02:   66 of  429 MB written (fifo 100%) [buf  99%]   4.3x.
Track 02:   67 of  429 MB written (fifo 100%) [buf  98%]   4.1x.
Track 02:   68 of  429 MB written (fifo 100%) [buf  98%]   4.1x.
Track 02:   69 of  429 MB written (fifo 100%) [buf  98%]   4.1x.
Track 02:   70 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   71 of  429 MB written (fifo 100%) [buf  98%]   4.0x.
Track 02:   72 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   73 of  429 MB written (fifo 100%) [buf  99%]   4.0x.
Track 02:   74 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   75 of  429 MB written (fifo  99%) [buf  98%]   4.0x.
Track 02:   76 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   77 of  429 MB written (fifo  99%) [buf  96%]   3.9x.
Track 02:   78 of  429 MB written (fifo 100%) [buf  98%]   4.3x.
Track 02:   79 of  429 MB written (fifo 100%) [buf  94%]   3.8x.
Track 02:   80 of  429 MB written (fifo 100%) [buf  98%]   4.4x.
Track 02:   81 of  429 MB written (fifo 100%) [buf  93%]   3.8x.
Track 02:   82 of  429 MB written (fifo 100%) [buf  98%]   4.5x.
Track 02:   83 of  429 MB written (fifo 100%) [buf  97%]   4.0x.
Track 02:   84 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   85 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   86 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   87 of  429 MB written (fifo 100%) [buf  98%]   4.2x.
Track 02:   88 of  429 MB written (fifo 100%) [buf  98%]   4.1x.
Track 02:   89 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   90 of  429 MB written (fifo 100%) [buf  98%]   4.1x.
Track 02:   91 of  429 MB written (fifo 100%) [buf  99%]   4.3x.
Track 02:   92 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   93 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   94 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   95 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   96 of  429 MB written (fifo 100%) [buf  98%]   4.1x.
Track 02:   97 of  429 MB written (fifo 100%) [buf  98%]   4.1x.
Track 02:   98 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   99 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:  100 of  429 MB written (fifo  96%) [buf  98%]   4.1x.
Track 02:  101 of  429 MB written (fifo  94%) [buf  98%]   4.2x.
Track 02:  102 of  429 MB written (fifo  98%) [buf  99%]   4.1x.
Track 02:  103 of  429 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:  104 of  429 MB written (fifo  95%) [buf  99%]   4.1x.
Track 02:  105 of  429 MB written (fifo  96%) [buf  99%]   4.2x.
Track 02:  106 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:  107 of  429 MB written (fifo 100%) [buf  98%]   4.2x.
Track 02:  108 of  429 MB written (fifo  98%) [buf  98%]   4.1x.
Track 02:  109 of  429 MB written (fifo 100%) [buf  97%]   4.2x.
Track 02:  110 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:  111 of  429 MB written (fifo  97%) [buf  97%]   4.2x.
Track 02:  112 of  429 MB written (fifo 100%) [buf  99%]   4.0x.
Track 02:  113 of  429 MB written (fifo  97%) [buf  98%]   4.2x.
Track 02:  114 of  429 MB written (fifo  98%) [buf  98%]   4.0x.
Track 02:  115 of  429 MB written (fifo  97%) [buf  99%]   4.2x.
Track 02:  116 of  429 MB written (fifo  97%) [buf  99%]   4.0x.
Track 02:  117 of  429 MB written (fifo 100%) [buf  98%]   4.2x.
Track 02:  118 of  429 MB written (fifo  98%) [buf  99%]   4.0x.
Track 02:  119 of  429 MB written (fifo 100%) [buf  98%]   4.1x.
Track 02:  120 of  429 MB written (fifo  96%) [buf  98%]   4.0x.
Track 02:  121 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:  122 of  429 MB written (fifo  98%) [buf  98%]   4.0x.
Track 02:  123 of  429 MB written (fifo 100%) [buf  98%]   4.1x.
Track 02:  124 of  429 MB written (fifo 100%) [buf  99%]   4.0x.
Track 02:  125 of  429 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:  126 of  429 MB written (fifo 100%) [buf  98%]   4.0x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 DE 30 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63504
cmd finished after 0.039s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 132723360 bytes
Writing  time:  244.368s
Average write speed  10.9x.
Min drive buffer fill was 93%
Fixating...
Fixating time:    0.018s

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=4 -dao cuefile=/home/sacha/television/Grays_Anatomy_s4e3.cue -eject 

Any thoughts on what's going wrong?

---

