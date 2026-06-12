---
title: "k3b Error- Code 254"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by ignignokt00 on 2007-06-19
I've been burning CDs out of mp3s with k3b for a long time with no trouble.  Seemingly out of the blue, CDs stop burning part of the way through, often at different places.
I've tried other CD-Rs with no avail.

k3b gives me this:

System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-15-generic
Devices
-----------------------
SAMSUNG DVD-ROM SD-616T F310 (/dev/scd0, ) [CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM] [None]

PHILIPS DVD+-RW DVD8631 BD10 (/dev/scd1, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R16, RAW/R96R, Restricted Overwrite]
Used versions
-----------------------
cdrecord: 1.1.2

cdrecord
-----------------------
scsidev: '/dev/scd1'
devname: '/dev/scd1'
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
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PHILIPS '
Identification : 'DVD+-RW DVD8631 '
Revision       : 'BD10'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 1073152 = 1048 KB
FIFO size      : 12582912 = 12288 KB
Track 01: audio   28 MB (02:50.77) no preemp swab     
Track 02: audio   39 MB (03:52.08) no preemp swab     
Track 03: audio   34 MB (03:26.06) no preemp swab     
Track 04: audio   36 MB (03:39.12) no preemp swab     
Track 05: audio   35 MB (03:30.10) no preemp swab     
Track 06: audio   40 MB (04:03.00) no preemp swab     
Track 07: audio   32 MB (03:14.69) no preemp swab     
Track 08: audio   20 MB (02:00.06) no preemp swab     
Track 09: audio   37 MB (03:40.53) no preemp swab     
Track 10: audio   33 MB (03:20.18) no preemp swab     
Track 11: audio   34 MB (03:25.58) no preemp swab     
Track 12: audio   30 MB (02:59.08) no preemp swab     
Track 13: audio   51 MB (05:08.06) no preemp swab     
Track 14: audio   49 MB (04:53.57) no preemp swab     
Track 15: audio   48 MB (04:47.82) no preemp swab     
Total size:      553 MB (54:50.76) = 246807 sectors
Lout start:      553 MB (54:52/57) = 246807 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 6
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type C, low Beta category (C-) (6)
  ATIP start of lead in:  -11231 (97:32/19)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 27
Manufacturer: Prodisc Technology Inc.
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 113039
Starting to write CD/DVD at speed  40.0 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
Speed set to 7056 KB/s
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Errno: 5 (Input/output error), read track info scsi sendcmd: no error
CDB:  52 01 00 00 00 FF 00 00 1C 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 12 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 28
cmd finished after 0.003s timeout 240s
/usr/bin/wodim: Cannot get next writable address for 'invisible' track.
/usr/bin/wodim: This means that we are checking recorded media.
/usr/bin/wodim: This media cannot be written in streaming mode anymore.
/usr/bin/wodim: If you like to write to 'preformatted' RW media, try to blank the media first.
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of   28 MB written.
Track 01:    1 of   28 MB written (fifo 100%) [buf  88%]  29.8x.
Track 01:    2 of   28 MB written (fifo  99%) [buf  93%]  18.8x.
Track 01:    3 of   28 MB written (fifo  99%) [buf  93%]  18.4x.
Track 01:    4 of   28 MB written (fifo 100%) [buf  89%]  17.2x.
Track 01:    5 of   28 MB written (fifo 100%) [buf  89%]  18.5x.
Track 01:    6 of   28 MB written (fifo  99%) [buf  95%]  18.9x.
Track 01:    7 of   28 MB written (fifo  99%) [buf  95%]  18.6x.
Track 01:    8 of   28 MB written (fifo 100%) [buf  91%]  17.3x.
Track 01:    9 of   28 MB written (fifo 100%) [buf  91%]  18.6x.
Track 01:   10 of   28 MB written (fifo 100%) [buf  96%]  19.0x.
Track 01:   11 of   28 MB written (fifo  99%) [buf  96%]  18.7x.
Track 01:   12 of   28 MB written (fifo 100%) [buf  92%]  17.5x.
Track 01:   13 of   28 MB written (fifo 100%) [buf  92%]  18.8x.
Track 01:   14 of   28 MB written (fifo 100%) [buf  88%]  17.4x.
Track 01:   15 of   28 MB written (fifo 100%) [buf  88%]  18.8x.
Track 01:   16 of   28 MB written (fifo  99%) [buf  93%]  19.3x.
Track 01:   17 of   28 MB written (fifo  99%) [buf  93%]  18.9x.
Track 01:   18 of   28 MB written (fifo 100%) [buf  89%]  17.7x.
Track 01:   19 of   28 MB written (fifo 100%) [buf  89%]  18.9x.
Track 01:   20 of   28 MB written (fifo 100%) [buf  94%]  19.4x.
Track 01:   21 of   28 MB written (fifo  99%) [buf  94%]  19.0x.
Track 01:   22 of   28 MB written (fifo 100%) [buf  90%]  17.8x.
Track 01:   23 of   28 MB written (fifo 100%) [buf  90%]  19.1x.
Track 01:   24 of   28 MB written (fifo  99%) [buf  95%]  19.5x.
Track 01:   25 of   28 MB written (fifo  99%) [buf  95%]  19.2x.
Track 01:   26 of   28 MB written (fifo 100%) [buf  91%]  17.9x.
Track 01:   27 of   28 MB written (fifo 100%) [buf  91%]  19.2x.
Track 01:   28 of   28 MB written (fifo  99%) [buf  96%]  19.6x.
Track 01: Total bytes read/written: 30124416/30124416 (12808 sectors).
Starting new track at sector: 12808
Track 02:    0 of   39 MB written.
Track 02:    1 of   39 MB written (fifo  99%) [buf  96%]   6.8x.
Track 02:    2 of   39 MB written (fifo 100%) [buf  92%]  18.5x.
Track 02:    3 of   39 MB written (fifo 100%) [buf  92%]  19.8x.
Track 02:    4 of   39 MB written (fifo 100%) [buf  88%]  18.4x.
Track 02:    5 of   39 MB written (fifo 100%) [buf  88%]  19.8x.
Track 02:    6 of   39 MB written (fifo  99%) [buf  93%]  20.3x.
Track 02:    7 of   39 MB written (fifo 100%) [buf  93%]  19.9x.
Track 02:    8 of   39 MB written (fifo 100%) [buf  89%]  18.6x.
Track 02:    9 of   39 MB written (fifo 100%) [buf  89%]  20.0x.
Track 02:   10 of   39 MB written (fifo  99%) [buf  94%]  20.4x.
Track 02:   11 of   39 MB written (fifo 100%) [buf  94%]  20.0x.
Track 02:   12 of   39 MB written (fifo 100%) [buf  90%]  18.7x.
Track 02:   13 of   39 MB written (fifo 100%) [buf  90%]  20.2x.
Track 02:   14 of   39 MB written (fifo  99%) [buf  95%]  20.6x.
Track 02:   15 of   39 MB written (fifo  99%) [buf  95%]  20.2x.
Track 02:   16 of   39 MB written (fifo 100%) [buf  91%]  18.8x.
Track 02:   17 of   39 MB written (fifo 100%) [buf  91%]  20.2x.
Track 02:   18 of   39 MB written (fifo  99%) [buf  96%]  20.7x.
Track 02:   19 of   39 MB written (fifo 100%) [buf  96%]  20.3x.
Track 02:   20 of   39 MB written (fifo 100%) [buf  92%]  19.0x.
Track 02:   21 of   39 MB written (fifo 100%) [buf  92%]  20.3x.
Track 02:   22 of   39 MB written (fifo 100%) [buf  88%]  18.9x.
Track 02:   23 of   39 MB written (fifo 100%) [buf  88%]  20.4x.
Track 02:   24 of   39 MB written (fifo  99%) [buf  94%]  20.9x.
Track 02:   25 of   39 MB written (fifo  99%) [buf  94%]  20.5x.
Track 02:   26 of   39 MB written (fifo 100%) [buf  90%]  19.2x.
Track 02:   27 of   39 MB written (fifo 100%) [buf  90%]  20.5x.
Track 02:   28 of   39 MB written (fifo  99%) [buf  95%]  21.0x.
Track 02:   29 of   39 MB written (fifo  99%) [buf  95%]  20.5x.
Track 02:   30 of   39 MB written (fifo 100%) [buf  91%]  19.3x.
Track 02:   31 of   39 MB written (fifo  99%) [buf  91%]  20.6x.
Track 02:   32 of   39 MB written (fifo  99%) [buf  96%]  21.1x.
Track 02:   33 of   39 MB written (fifo  99%) [buf  96%]  20.7x.
Track 02:   34 of   39 MB written (fifo 100%) [buf  92%]  19.3x.
Track 02:   35 of   39 MB written (fifo 100%) [buf  92%]  20.7x.
Track 02:   36 of   39 MB written (fifo 100%) [buf  88%]  19.3x.
Track 02:   37 of   39 MB written (fifo 100%) [buf  88%]  20.8x.
Track 02:   38 of   39 MB written (fifo  99%) [buf  93%]  21.3x.
Track 02:   39 of   39 MB written (fifo 100%) [buf  93%]  20.8x.
Track 02: Total bytes read/written: 40938912/40938912 (17406 sectors).
Starting new track at sector: 30214
Track 03:    0 of   34 MB written.
Track 03:    1 of   34 MB written (fifo 100%) [buf  92%]  19.9x.
Track 03:    2 of   34 MB written (fifo 100%) [buf  88%]  19.9x.
Track 03:    3 of   34 MB written (fifo 100%) [buf  88%]  21.5x.
Track 03:    4 of   34 MB written (fifo  99%) [buf  94%]  22.0x.
Track 03:    5 of   34 MB written (fifo  99%) [buf  94%]  21.6x.
Track 03:    6 of   34 MB written (fifo 100%) [buf  90%]  20.2x.
Track 03:    7 of   34 MB written (fifo 100%) [buf  90%]  21.7x.
Track 03:    8 of   34 MB written (fifo  99%) [buf  95%]  22.1x.
Track 03:    9 of   34 MB written (fifo  99%) [buf  95%]  21.7x.
Track 03:   10 of   34 MB written (fifo 100%) [buf  91%]  20.3x.
Track 03:   11 of   34 MB written (fifo 100%) [buf  91%]  21.7x.
Track 03:   12 of   34 MB written (fifo  99%) [buf  96%]  22.2x.
Track 03:   13 of   34 MB written (fifo  99%) [buf  96%]  21.8x.
Track 03:   14 of   34 MB written (fifo 100%) [buf  92%]  20.4x.
Track 03:   15 of   34 MB written (fifo 100%) [buf  92%]  21.9x.
Track 03:   16 of   34 MB written (fifo 100%) [buf  88%]  20.3x.
Track 03:   17 of   34 MB written (fifo 100%) [buf  88%]  21.9x.
Track 03:   18 of   34 MB written (fifo  99%) [buf  93%]  22.3x.
Track 03:   19 of   34 MB written (fifo  99%) [buf  93%]  22.0x.
Track 03:   20 of   34 MB written (fifo 100%) [buf  89%]   6.2x.
Track 03:   21 of   34 MB written (fifo 100%) [buf  89%]  22.0x.
Track 03:   22 of   34 MB written (fifo  99%) [buf  94%]  22.5x.
Track 03:   23 of   34 MB written (fifo  99%) [buf  94%]  22.0x.
Track 03:   24 of   34 MB written (fifo 100%) [buf  90%]  20.7x.
Track 03:   25 of   34 MB written (fifo 100%) [buf  90%]  22.1x.
Track 03:   26 of   34 MB written (fifo 100%) [buf  95%]  22.6x.
Track 03:   27 of   34 MB written (fifo  99%) [buf  95%]  22.1x.
Track 03:   28 of   34 MB written (fifo 100%) [buf  91%]  20.7x.
Track 03:   29 of   34 MB written (fifo 100%) [buf  91%]  22.2x.
Track 03:   30 of   34 MB written (fifo  99%) [buf  96%]  22.7x.
Track 03:   31 of   34 MB written (fifo  99%) [buf  96%]  22.3x.
Track 03:   32 of   34 MB written (fifo 100%) [buf  92%]  20.8x.
Track 03:   33 of   34 MB written (fifo 100%) [buf  92%]  22.3x.
Track 03:   34 of   34 MB written (fifo 100%) [buf  88%]  20.7x.
Track 03: Total bytes read/written: 36350160/36350160 (15455 sectors).
Starting new track at sector: 45669
Track 04:    0 of   36 MB written.
Track 04:    1 of   36 MB written (fifo 100%) [buf  92%]  21.1x.
Track 04:    2 of   36 MB written (fifo 100%) [buf  88%]  21.3x.
Track 04:    3 of   36 MB written (fifo 100%) [buf  88%]  23.0x.
Track 04:    4 of   36 MB written (fifo  99%) [buf  93%]  23.4x.
Track 04:    5 of   36 MB written (fifo  99%) [buf  93%]  23.0x.
Track 04:    6 of   36 MB written (fifo 100%) [buf  89%]  21.5x.
Track 04:    7 of   36 MB written (fifo 100%) [buf  89%]  23.1x.
Track 04:    8 of   36 MB written (fifo  99%) [buf  95%]  23.5x.
Track 04:    9 of   36 MB written (fifo  99%) [buf  95%]  23.1x.
Track 04:   10 of   36 MB written (fifo 100%) [buf  91%]  21.6x.
Track 04:   11 of   36 MB written (fifo 100%) [buf  91%]  23.1x.
Track 04:   12 of   36 MB written (fifo  99%) [buf  96%]  23.6x.
Track 04:   13 of   36 MB written (fifo  99%) [buf  96%]  23.1x.
Track 04:   14 of   36 MB written (fifo  98%) [buf  92%]  21.8x.
Track 04:   15 of   36 MB written (fifo 100%) [buf  92%]  23.2x.
Track 04:   16 of   36 MB written (fifo 100%) [buf  88%]  21.6x.
Track 04:   17 of   36 MB written (fifo 100%) [buf  88%]  23.3x.
Track 04:   18 of   36 MB written (fifo 100%) [buf  93%]  23.8x.
Track 04:   19 of   36 MB written (fifo  99%) [buf  93%]  23.4x.
Track 04:   20 of   36 MB written (fifo  99%) [buf  89%]  21.8x.
Track 04:   21 of   36 MB written (fifo 100%) [buf  89%]  23.4x.
Track 04:   22 of   36 MB written (fifo  99%) [buf  94%]  23.8x.
Track 04:   23 of   36 MB written (fifo  99%) [buf  94%]  23.3x.
Track 04:   24 of   36 MB written (fifo 100%) [buf  90%]  22.0x.
Track 04:   25 of   36 MB written (fifo 100%) [buf  90%]  23.5x.
Track 04:   26 of   36 MB written (fifo  99%) [buf  95%]  24.0x.
Track 04:   27 of   36 MB written (fifo  99%) [buf  95%]  23.5x.
Track 04:   28 of   36 MB written (fifo 100%) [buf  91%]  22.0x.
Track 04:   29 of   36 MB written (fifo 100%) [buf  91%]  23.5x.
Track 04:   30 of   36 MB written (fifo  99%) [buf  96%]  24.0x.
Track 04:   31 of   36 MB written (fifo  99%) [buf  96%]  23.7x.
Track 04:   32 of   36 MB written (fifo  99%) [buf  92%]  22.0x.
Track 04:   33 of   36 MB written (fifo 100%) [buf  92%]  23.7x.
Track 04:   34 of   36 MB written (fifo 100%) [buf  88%]  21.9x.
Track 04:   35 of   36 MB written (fifo 100%) [buf  88%]  23.7x.
Track 04:   36 of   36 MB written (fifo  99%) [buf  93%]  24.2x.
Track 04: Total bytes read/written: 38652768/38652768 (16434 sectors).
Starting new track at sector: 62103
Track 05:    0 of   35 MB written.
Track 05:    1 of   35 MB written (fifo 100%) [buf  96%]  24.2x.
Track 05:    2 of   35 MB written (fifo 100%) [buf  92%]  22.8x.
Track 05:    3 of   35 MB written (fifo 100%) [buf  92%]  24.4x.
Track 05:    4 of   35 MB written (fifo 100%) [buf  88%]  22.7x.
Track 05:    5 of   35 MB written (fifo 100%) [buf  88%]  24.4x.
Track 05:    6 of   35 MB written (fifo  99%) [buf  93%]  24.9x.
Track 05:    7 of   35 MB written (fifo  99%) [buf  93%]  24.4x.
Track 05:    8 of   35 MB written (fifo 100%) [buf  89%]  23.0x.
Track 05:    9 of   35 MB written (fifo  99%) [buf  89%]  24.5x.
Track 05:   10 of   35 MB written (fifo  98%) [buf  94%]  25.0x.
Track 05:   11 of   35 MB written (fifo  99%) [buf  94%]  24.6x.
Track 05:   12 of   35 MB written (fifo 100%) [buf  90%]  23.0x.
Track 05:   13 of   35 MB written (fifo 100%) [buf  90%]  24.6x.
Track 05:   14 of   35 MB written (fifo  99%) [buf  95%]  25.0x.
Track 05:   15 of   35 MB written (fifo  99%) [buf  95%]  24.7x.
Track 05:   16 of   35 MB written (fifo 100%) [buf  91%]   1.4x.
Track 05:   17 of   35 MB written (fifo  99%) [buf  91%]  26.2x.
Track 05:   18 of   35 MB written (fifo  99%) [buf  96%]  25.2x.
Track 05:   19 of   35 MB written (fifo  99%) [buf  96%]  24.7x.
Track 05:   20 of   35 MB written (fifo 100%) [buf  92%]  23.1x.
Track 05:   21 of   35 MB written (fifo 100%) [buf  92%]  24.8x.
Track 05:   22 of   35 MB written (fifo 100%) [buf  88%]  22.9x.
Track 05:   23 of   35 MB written (fifo 100%) [buf  88%]  24.9x.
Track 05:   24 of   35 MB written (fifo 100%) [buf  93%]  25.1x.
Track 05:   25 of   35 MB written (fifo 100%) [buf  93%]  25.1x.
Track 05:   26 of   35 MB written (fifo 100%) [buf  89%]  23.2x.
Track 05:   27 of   35 MB written (fifo  99%) [buf  89%]  24.9x.
Track 05:   28 of   35 MB written (fifo  99%) [buf  95%]  25.3x.
Track 05:   29 of   35 MB written (fifo  99%) [buf  95%]  24.9x.
Track 05:   30 of   35 MB written (fifo 100%) [buf  91%]  23.3x.
Track 05:   31 of   35 MB written (fifo 100%) [buf  91%]  24.9x.
Track 05:   32 of   35 MB written (fifo  99%) [buf  96%]  25.4x.
Track 05:   33 of   35 MB written (fifo  99%) [buf  96%]  25.0x.
Track 05:   34 of   35 MB written (fifo 100%) [buf  92%]  23.4x.
Track 05:   35 of   35 MB written (fifo 100%) [buf  92%]  25.1x.
Track 05: Total bytes read/written: 37062816/37062816 (15758 sectors).
Starting new track at sector: 77861
Track 06:    0 of   40 MB written.
Track 06:    1 of   40 MB written (fifo 100%) [buf  89%]  23.5x.
Track 06:    2 of   40 MB written (fifo  99%) [buf  94%]  26.2x.
Track 06:    3 of   40 MB written (fifo  99%) [buf  94%]  25.7x.
Track 06:    4 of   40 MB written (fifo 100%) [buf  90%]  24.1x.
Track 06:    5 of   40 MB written (fifo 100%) [buf  90%]  25.7x.
Track 06:    6 of   40 MB written (fifo  99%) [buf  95%]  26.1x.
Track 06:    7 of   40 MB written (fifo  99%) [buf  95%]  25.9x.
Track 06:    8 of   40 MB written (fifo 100%) [buf  91%]  24.2x.
Track 06:    9 of   40 MB written (fifo 100%) [buf  91%]  25.8x.
Track 06:   10 of   40 MB written (fifo 100%) [buf  87%]  23.9x.
Track 06:   11 of   40 MB written (fifo 100%) [buf  87%]  25.8x.
Track 06:   12 of   40 MB written (fifo  99%) [buf  93%]  26.3x.
Track 06:   13 of   40 MB written (fifo  99%) [buf  93%]  26.0x.
Track 06:   14 of   40 MB written (fifo 100%) [buf  89%]  24.3x.
Track 06:   15 of   40 MB written (fifo 100%) [buf  89%]  25.9x.
Track 06:   16 of   40 MB written (fifo  99%) [buf  94%]  26.4x.
Track 06:   17 of   40 MB written (fifo  99%) [buf  94%]  25.9x.
Track 06:   18 of   40 MB written (fifo 100%) [buf  90%]  24.3x.
Track 06:   19 of   40 MB written (fifo 100%) [buf  90%]  25.9x.
Track 06:   20 of   40 MB written (fifo  99%) [buf  95%]  26.6x.
Track 06:   21 of   40 MB written (fifo  99%) [buf  95%]  26.0x.
Track 06:   22 of   40 MB written (fifo 100%) [buf  91%]  24.4x.
Track 06:   23 of   40 MB written (fifo  99%) [buf  91%]  26.0x.
Track 06:   24 of   40 MB written (fifo  99%) [buf  96%]  26.6x.
Track 06:   25 of   40 MB written (fifo  99%) [buf  96%]  26.1x.
Track 06:   26 of   40 MB written (fifo 100%) [buf  92%]  24.4x.
Track 06:   27 of   40 MB written (fifo 100%) [buf  92%]  26.1x.
Track 06:   28 of   40 MB written (fifo 100%) [buf  88%]  24.2x.
Track 06:   29 of   40 MB written (fifo 100%) [buf  88%]  26.1x.
Track 06:   30 of   40 MB written (fifo  99%) [buf  93%]  26.5x.
Track 06:   31 of   40 MB written (fifo  99%) [buf  93%]  26.3x.
Track 06:   32 of   40 MB written (fifo 100%) [buf  89%]  24.5x.
Track 06:   33 of   40 MB written (fifo  99%) [buf  89%]  26.2x.
Track 06:   34 of   40 MB written (fifo  99%) [buf  94%]  26.7x.
Track 06:   35 of   40 MB written (fifo  99%) [buf  94%]  26.2x.
Track 06:   36 of   40 MB written (fifo 100%) [buf  90%]  24.6x.
Track 06:   37 of   40 MB written (fifo  99%) [buf  90%]  26.3x.
Track 06:   38 of   40 MB written (fifo  99%) [buf  95%]  26.7x.
Track 06:   39 of   40 MB written (fifo  99%) [buf  95%]  26.3x.
Track 06:   40 of   40 MB written (fifo 100%) [buf  91%]  24.6x.
Track 06: Total bytes read/written: 42865200/42865200 (18225 sectors).
Starting new track at sector: 96086
Track 07:    0 of   32 MB written.
Track 07:    1 of   32 MB written (fifo  98%) [buf  95%]  27.0x.
Track 07:    2 of   32 MB written (fifo 100%) [buf  91%]  25.4x.
Track 07:    3 of   32 MB written (fifo 100%) [buf  91%]  27.2x.
Track 07:    4 of   32 MB written (fifo 100%) [buf  87%]  25.2x.
Track 07:    5 of   32 MB written (fifo 100%) [buf  87%]  27.2x.
Track 07:    6 of   32 MB written (fifo  99%) [buf  93%]  27.6x.
Track 07:    7 of   32 MB written (fifo  99%) [buf  93%]  27.2x.
Track 07:    8 of   32 MB written (fifo 100%) [buf  89%]  25.4x.
Track 07:    9 of   32 MB written (fifo  99%) [buf  89%]  27.3x.
Track 07:   10 of   32 MB written (fifo  98%) [buf  94%]  27.7x.
Track 07:   11 of   32 MB written (fifo  99%) [buf  94%]  27.2x.
Track 07:   12 of   32 MB written (fifo 100%) [buf  90%]  25.5x.
Track 07:   13 of   32 MB written (fifo 100%) [buf  90%]  27.3x.
Track 07:   14 of   32 MB written (fifo 100%) [buf  95%]  27.7x.
Track 07:   15 of   32 MB written (fifo  99%) [buf  95%]  27.4x.
Track 07:   16 of   32 MB written (fifo 100%) [buf  91%]  25.6x.
Track 07:   17 of   32 MB written (fifo 100%) [buf  91%]  27.3x.
Track 07:   18 of   32 MB written (fifo  99%) [buf  96%]  27.7x.
Track 07:   19 of   32 MB written (fifo  99%) [buf  96%]  27.5x.
Track 07:   20 of   32 MB written (fifo 100%) [buf  92%]   7.1x.
Track 07:   21 of   32 MB written (fifo 100%) [buf  92%]  27.4x.
Track 07:   22 of   32 MB written (fifo 100%) [buf  88%]  25.4x.
Track 07:   23 of   32 MB written (fifo 100%) [buf  88%]  27.4x.
Track 07:   24 of   32 MB written (fifo  99%) [buf  93%]  27.9x.
Track 07:   25 of   32 MB written (fifo  99%) [buf  93%]  27.4x.
Track 07:   26 of   32 MB written (fifo  99%) [buf  89%]  25.8x.
Track 07:   27 of   32 MB written (fifo 100%) [buf  89%]  27.5x.
Track 07:   28 of   32 MB written (fifo  99%) [buf  94%]  27.9x.
Track 07:   29 of   32 MB written (fifo  99%) [buf  94%]  27.5x.
Track 07:   30 of   32 MB written (fifo 100%) [buf  90%]  25.7x.
Track 07:   31 of   32 MB written (fifo 100%) [buf  90%]  27.6x.
Track 07:   32 of   32 MB written (fifo  99%) [buf  95%]  27.9x.
Track 07: Total bytes read/written: 34343904/34343904 (14602 sectors).
Starting new track at sector: 110688
Track 08:    0 of   20 MB written.
Track 08:    1 of   20 MB written (fifo 100%) [buf  88%]  25.8x.
Track 08:    2 of   20 MB written (fifo  99%) [buf  93%]  28.8x.
Track 08:    3 of   20 MB written (fifo  99%) [buf  93%]  28.2x.
Track 08:    4 of   20 MB written (fifo 100%) [buf  89%]  26.5x.
Track 08:    5 of   20 MB written (fifo  98%) [buf  89%]  28.2x.
Track 08:    6 of   20 MB written (fifo  99%) [buf  95%]  28.7x.
Track 08:    7 of   20 MB written (fifo  99%) [buf  95%]  28.3x.
Track 08:    8 of   20 MB written (fifo 100%) [buf  91%]  26.5x.
Track 08:    9 of   20 MB written (fifo 100%) [buf  91%]  28.3x.
Track 08:   10 of   20 MB written (fifo  99%) [buf  96%]  28.8x.
Track 08:   11 of   20 MB written (fifo  99%) [buf  96%]  28.3x.
Track 08:   12 of   20 MB written (fifo 100%) [buf  92%]  26.5x.
Track 08:   13 of   20 MB written (fifo 100%) [buf  92%]  28.4x.
Track 08:   14 of   20 MB written (fifo 100%) [buf  88%]  26.3x.
Track 08:   15 of   20 MB written (fifo 100%) [buf  88%]  28.4x.
Track 08:   16 of   20 MB written (fifo  99%) [buf  93%]  28.9x.
Track 08:   17 of   20 MB written (fifo  99%) [buf  93%]  28.3x.
Track 08:   18 of   20 MB written (fifo  98%) [buf  89%]  26.7x.
Track 08:   19 of   20 MB written (fifo  99%) [buf  89%]  28.4x.
Track 08:   20 of   20 MB written (fifo  99%) [buf  94%]  28.9x.
Track 08: Total bytes read/written: 21179760/21179760 (9005 sectors).
Starting new track at sector: 119693
Track 09:    0 of   37 MB written.
Track 09:    1 of   37 MB written (fifo  98%) [buf  94%]  28.6x.
Track 09:    2 of   37 MB written (fifo 100%) [buf  90%]  27.1x.
Track 09:    3 of   37 MB written (fifo 100%) [buf  90%]  28.9x.
Track 09:    4 of   37 MB written (fifo  99%) [buf  95%]  29.4x.
Track 09:    5 of   37 MB written (fifo  98%) [buf  95%]  28.9x.
Track 09:    6 of   37 MB written (fifo  98%) [buf  91%]  27.1x.
Track 09:    7 of   37 MB written (fifo 100%) [buf  91%]  29.0x.
Track 09:    8 of   37 MB written (fifo  99%) [buf  96%]  29.4x.
Track 09:    9 of   37 MB written (fifo  99%) [buf  96%]  29.0x.
Track 09:   10 of   37 MB written (fifo 100%) [buf  92%]  27.1x.
Track 09:   11 of   37 MB written (fifo 100%) [buf  92%]  28.9x.
Track 09:   12 of   37 MB written (fifo 100%) [buf  88%]  26.9x.
Track 09:   13 of   37 MB written (fifo 100%) [buf  88%]  29.0x.
Track 09:   14 of   37 MB written (fifo 100%) [buf  93%]  29.5x.
Track 09:   15 of   37 MB written (fifo  99%) [buf  93%]  28.9x.
Track 09:   16 of   37 MB written (fifo 100%) [buf  89%]  27.3x.
Track 09:   17 of   37 MB written (fifo  99%) [buf  89%]  28.9x.
Track 09:   18 of   37 MB written (fifo  99%) [buf  94%]  29.7x.
Track 09:   19 of   37 MB written (fifo  99%) [buf  94%]  29.0x.
Track 09:   20 of   37 MB written (fifo 100%) [buf  90%]  27.2x.
Track 09:   21 of   37 MB written (fifo 100%) [buf  90%]  29.1x.
Track 09:   22 of   37 MB written (fifo  98%) [buf  95%]  29.5x.
Track 09:   23 of   37 MB written (fifo  99%) [buf  95%]  29.1x.
Track 09:   24 of   37 MB written (fifo 100%) [buf  91%]  27.3x.
Track 09:   25 of   37 MB written (fifo  98%) [buf  91%]  29.1x.
Track 09:   26 of   37 MB written (fifo 100%) [buf  87%]  27.0x.
Track 09:   27 of   37 MB written (fifo  99%) [buf  87%]  29.1x.
Track 09:   28 of   37 MB written (fifo  99%) [buf  93%]  29.6x.
Track 09:   29 of   37 MB written (fifo  99%) [buf  93%]  29.1x.
Track 09:   30 of   37 MB written (fifo 100%) [buf  89%]  27.4x.
Track 09:   31 of   37 MB written (fifo 100%) [buf  89%]  29.2x.
Track 09:   32 of   37 MB written (fifo  98%) [buf  94%]  29.7x.
Track 09:   33 of   37 MB written (fifo  99%) [buf  94%]  29.2x.
Track 09:   34 of   37 MB written (fifo 100%) [buf  90%]  27.3x.
Track 09:   35 of   37 MB written (fifo 100%) [buf  90%]  29.4x.
Track 09:   36 of   37 MB written (fifo  99%) [buf  95%]  29.7x.
Track 09:   37 of   37 MB written (fifo  99%) [buf  95%]  29.2x.
Track 09: Total bytes read/written: 38902080/38902080 (16540 sectors).
Starting new track at sector: 136233
Track 10:    0 of   33 MB written.
Track 10:    1 of   33 MB written (fifo 100%) [buf  90%]  27.7x.
Track 10:    2 of   33 MB written (fifo  98%) [buf  95%]  30.5x.
Track 10:    3 of   33 MB written (fifo  98%) [buf  95%]  30.1x.
Track 10:    4 of   33 MB written (fifo 100%) [buf  91%]  28.2x.
Track 10:    5 of   33 MB written (fifo  99%) [buf  91%]  30.1x.
Track 10:    6 of   33 MB written (fifo  99%) [buf  96%]  30.5x.
Track 10:    7 of   33 MB written (fifo  99%) [buf  96%]  30.1x.
Track 10:    8 of   33 MB written (fifo 100%) [buf  92%]  28.2x.
Track 10:    9 of   33 MB written (fifo 100%) [buf  92%]  30.1x.
Track 10:   10 of   33 MB written (fifo 100%) [buf  88%]  27.9x.
Track 10:   11 of   33 MB written (fifo 100%) [buf  88%]  30.1x.
Track 10:   12 of   33 MB written (fifo 100%) [buf  93%]  30.5x.
Track 10:   13 of   33 MB written (fifo  99%) [buf  93%]  30.3x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 02 2B C9 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 03 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x03 (setmark detected) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63504
cmd finished after 230.809s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 14224896 bytes
Writing  time:  356.643s
Average write speed   9.3x.
Min drive buffer fill was 87%
Fixating...
Fixating time:    0.007s

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd1 speed=40 -dao driveropts=burnfree -eject -useinfo -audio /media/cygnus/.tmp/k3b_audio_1_01.inf /media/cygnus/.tmp/k3b_audio_1_02.inf /media/cygnus/.tmp/k3b_audio_1_03.inf /media/cygnus/.tmp/k3b_audio_1_04.inf /media/cygnus/.tmp/k3b_audio_1_05.inf /media/cygnus/.tmp/k3b_audio_1_06.inf /media/cygnus/.tmp/k3b_audio_1_07.inf /media/cygnus/.tmp/k3b_audio_1_08.inf /media/cygnus/.tmp/k3b_audio_1_09.inf /media/cygnus/.tmp/k3b_audio_1_10.inf /media/cygnus/.tmp/k3b_audio_1_11.inf /media/cygnus/.tmp/k3b_audio_1_12.inf /media/cygnus/.tmp/k3b_audio_1_13.inf /media/cygnus/.tmp/k3b_audio_1_14.inf /media/cygnus/.tmp/k3b_audio_1_15.inf 


> cdrecord returned an unknown error (code 254).
Sometimes using TAO writing resolves this issue.

I have about 8 or 9 coasters out of a new pack of CD-Rs.  Please help.

---

### Post by ignignokt00 on 2007-06-21
bump

---

### Post by ignignokt00 on 2007-06-21
Bump again, someone please help.  I've searched to death and found nothing conclusive.  I'm tired of throwing new CD-R's into the garbage.

---

### Post by sunshine12 on 2007-06-24
having the same error while burning .iso image...

cd record returned an unknown error code:254
sometimes TAO writing mode resolves this issue

tried 2 cds and both stopped after 200MB of burning

If you find solution then please let me know, still searching..
Thanks

---

### Post by struess on 2007-06-24
same situation here, except with an audio cd.  this has never happened before, and i've burned tons of cds... i didn't change anything on my system (to my knowledge), so i don't know what started this problem.

k3b says "sometimes TAO writing mode solves this issue"... well, it doesn't for me.  nor does burning at slower speeds.  (i usually burn at 40x -- i tried burning at 8x last time and it suggested i "try burning at a slower speed."  >< )

i don't have any luck burning in gnomebaker, brasero, or serpentine either.  i'm making a mountain of coasters.  i don't think my firmware is out of date, and i've tried running the burning programs with *gksu*.  any help would be greatly appreciated..

---

### Post by ignignokt00 on 2007-06-24
You have the same exact problem as me.

Cmon guys, help?  Ubuntu is always praised for its excellent community support, but none of the help threads I've made here have had any replies.

---

### Post by struess on 2007-06-24
come to think of it, i did install updates recently from ubuntu update manager... is it possible something in there messed with cd-burner drivers?  ..or changed a library that gnomebaker/k3b/etc. use?

edit:  thinking a little bit harder, i haven't burned a cd in maybe two weeks.  the hunt through synaptic's update history might take a little while..

---

### Post by ignignokt00 on 2007-06-24
I got help from someone in #ubuntu, and I'm burning now. :D

first, I did:
ls -l /dev/`readlink /dev/cdrom`
to determine what group I should belong to to burn.  It was the "cdrom" group.

I added a "cdrom" group and added myself to it in Administration>Users and Groups.

sudo chown root:cdrom /dev/scd1
sudo chmod g+x /dev/scd1

Logged out and in, and now I've burned a couple audio CDs with no problem.

edit: :( after two successful Audio CD burns at 8x and 24x, one at 40x failed with the old error.  I'm retrying at 8x now...

edit 2: 8x worked.  I guess was wrong about my drive's abilities.

---

### Post by struess on 2007-06-25
ignignokt00, i'm looking forward to trying your method.  (my cd's device ID is /dev/hda, but it sounds like it should still work.)

i didn't know how extensive this problem was, but it doesn't appear to affect (my) dvd burning.  just successfully toasted a dvd full of pictures using gnomebaker on full speed.. i'd use k3b, but all this tinkering has given me a DMA problem that i haven't yet fixed.  anyway, it's good to know dvd-burning is still functional. 

come to think of it, i haven't tried burning pictures onto a CD-R.  is it only audio CDs that are giving people trouble?

---

### Post by struess on 2007-06-25
hmm.. when i try to make a group in System --> Administration --> Users and Groups called "cdrom", and add root and myself as users, it doesn't stick.  i log out and log back in and the group "cdrom" is no longer there.  any idea what the reason is for this?

---

### Post by ignignokt00 on 2007-06-27
Yeah, the cdrom group disappeared here too.. :\  Problem most definitely not solved.

struess: I'm sure so far that audio CDs and data CDs don't work as they should.  I burned a data DVD earlier today, but it seems inconsistent.

---

### Post by Saitam72 on 2008-01-20
Just in case someone is reading this thread, experiencing all the phenomenons described here, and finding no sattisfying solution just as I did a few weeks ago: What helped on my system (Ubuntu 7.10 on AMD 64bit) was to turn the DMA mode for the CD drive OFF! I experience tiny interrupts when watching videos with DMA tured off. But burning CDs works fine in k3b and Serpentine.
You can turn the DMA mode for the CD drive (/dev/hdc) off by executing as root:
```
hdparm -d 0 /dev/hdc
```
To turn it off generally when starting the system I added the following lines to /etc/hdparm.conf:
```
command_line {
       hdparm -d 0 /dev/hdc
}
```

---

