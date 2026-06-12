---
title: "K3b closes session"
date: 2007-02-04
forum: Multimedia &amp; Video
---

### Post by angelmb on 2007-02-04
Hi, I am another proud user of Ubuntu Dapper. I have however an important issue with k3b when trying to burn an audio CD out of mp3 files. The problem is that k3b starts decoding correctly and recording correctly. After a couple or 3 songs it automatically closes the recording session and screws everything up (already screwed 12 CDs!!!!).

The error that k3b provides is (sorry for the length!):

System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-27-386
Devices
-----------------------
MATSHITA UJ-840D 1.00 (/dev/hdb, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Secuencial; DVD-RW sobreescritura restringida; DVD-RW Secuencial; DVD+RW; DVD+R; DVD+R doble capa; CD-ROM; CD-R; CD-RW] [SAO; TAO; Sobreescritura restringida]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-27-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/X11/cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
/usr/bin/X11/cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 0 = CD-DA
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identifikation : 'UJ-840D         '
Revision       : '1.00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0013 
Profile: 0x0014 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO
Drive buf size : 1310720 = 1280 KB
FIFO size      : 4194304 = 4096 KB
pregap1: -1
Track 01: audio   52 MB (05:11.93) no preemp copy
Track 02: audio   45 MB (04:32.93) no preemp copy
Track 03: audio   51 MB (05:07.16) no preemp copy
Track 04: audio   46 MB (04:39.25) no preemp copy
Track 05: audio   44 MB (04:22.74) no preemp copy
Track 06: audio   59 MB (05:52.89) no preemp copy
Track 07: audio   50 MB (05:01.38) no preemp copy
Track 08: audio   42 MB (04:14.41) no preemp copy
Track 09: audio   50 MB (04:57.46) no preemp copy
Track 10: audio   54 MB (05:21.76) no preemp copy
Track 11: audio   49 MB (04:52.89) no preemp copy
Track 12: audio   54 MB (05:24.21) no preemp copy
Track 13: audio   45 MB (04:32.41) no preemp copy
Track 14: audio   42 MB (04:14.85) no preemp copy
Total size:      690 MB (68:26.32) = 307974 sectors
Lout start:      691 MB (68:28/24) = 307974 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 51872
Starting to write CD/DVD at speed 24 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Sending CUE sheet...
/usr/bin/X11/cdrecord: WARNING: Drive returns wrong startsec (0) using -150
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of   52 MB written.
Track 01:    1 of   52 MB written (fifo 100%) [buf  98%]   7.9x.
Track 01:    2 of   52 MB written (fifo 100%) [buf  95%]   8.1x.
Track 01:    3 of   52 MB written (fifo 100%) [buf  97%]   8.5x.
Track 01:    4 of   52 MB written (fifo 100%) [buf  97%]   8.1x.
Track 01:    5 of   52 MB written (fifo 100%) [buf  99%]   8.8x.
Track 01:    6 of   52 MB written (fifo 100%) [buf  98%]   8.1x.
Track 01:    7 of   52 MB written (fifo 100%) [buf  98%]   8.5x.
Track 01:    8 of   52 MB written (fifo  98%) [buf  92%]   8.1x.
Track 01:    9 of   52 MB written (fifo 100%) [buf  97%]   8.5x.
Track 01:   10 of   52 MB written (fifo  98%) [buf  99%]   8.4x.
Track 01:   11 of   52 MB written (fifo 100%) [buf  99%]   8.2x.
Track 01:   12 of   52 MB written (fifo 100%) [buf  98%]   8.3x.
Track 01:   13 of   52 MB written (fifo 100%) [buf  98%]   8.4x.
Track 01:   14 of   52 MB written (fifo 100%) [buf  95%]   8.1x.
Track 01:   15 of   52 MB written (fifo 100%) [buf  98%]   8.4x.
Track 01:   16 of   52 MB written (fifo 100%) [buf  97%]   8.3x.
Track 01:   17 of   52 MB written (fifo 100%) [buf  97%]   8.0x.
Track 01:   18 of   52 MB written (fifo 100%) [buf  99%]   8.4x.
Track 01:   19 of   52 MB written (fifo 100%) [buf  99%]   8.4x.
Track 01:   20 of   52 MB written (fifo 100%) [buf  95%]   8.0x.
Track 01:   21 of   52 MB written (fifo 100%) [buf  98%]   8.4x.
Track 01:   22 of   52 MB written (fifo 100%) [buf  97%]   8.3x.
Track 01:   23 of   52 MB written (fifo 100%) [buf  97%]   8.1x.
Track 01:   24 of   52 MB written (fifo  98%) [buf  96%]   8.3x.
Track 01:   25 of   52 MB written (fifo 100%) [buf  99%]   8.4x.
Track 01:   26 of   52 MB written (fifo 100%) [buf  95%]   8.0x.
Track 01:   27 of   52 MB written (fifo 100%) [buf  98%]   8.3x.
Track 01:   28 of   52 MB written (fifo 100%) [buf  92%]   8.0x.
Track 01:   29 of   52 MB written (fifo 100%) [buf  97%]   8.3x.
Track 01:   30 of   52 MB written (fifo 100%) [buf  99%]   8.3x.
Track 01:   31 of   52 MB written (fifo 100%) [buf  99%]   8.0x.
Track 01:   32 of   52 MB written (fifo  98%) [buf  98%]   8.2x.
Track 01:   33 of   52 MB written (fifo 100%) [buf  98%]   8.3x.
Track 01:   34 of   52 MB written (fifo 100%) [buf  95%]   8.0x.
Track 01:   35 of   52 MB written (fifo 100%) [buf  97%]   8.3x.
Track 01:   36 of   52 MB written (fifo 100%) [buf  97%]   8.2x.
Track 01:   37 of   52 MB written (fifo 100%) [buf  97%]   7.9x.
Track 01:   38 of   52 MB written (fifo 100%) [buf  96%]   8.3x.
Track 01:   39 of   52 MB written (fifo 100%) [buf  98%]   2.2x.
Track 01:   40 of   52 MB written (fifo 100%) [buf  95%]  11.9x.
Track 01:   41 of   52 MB written (fifo 100%) [buf  97%]  12.3x.
Track 01:   42 of   52 MB written (fifo 100%) [buf  99%]  12.4x.
Track 01:   43 of   52 MB written (fifo 100%) [buf  98%]  12.2x.
Track 01:   44 of   52 MB written (fifo  98%) [buf  98%]  12.7x.
Track 01:   45 of   52 MB written (fifo 100%) [buf  95%]  12.2x.
Track 01:   46 of   52 MB written (fifo 100%) [buf  98%]  12.7x.
Track 01:   47 of   52 MB written (fifo 100%) [buf  99%]  12.6x.
Track 01:   48 of   52 MB written (fifo 100%) [buf  97%]  12.2x.
Track 01:   49 of   52 MB written (fifo 100%) [buf  99%]  12.6x.
Track 01:   50 of   52 MB written (fifo 100%) [buf  96%]  12.7x.
Track 01:   51 of   52 MB written (fifo 100%) [buf  93%]  12.1x.
Track 01:   52 of   52 MB written (fifo 100%) [buf  98%]  12.6x.
Track 01: Total bytes read/written: 55025040/55025040 (23395 sectors).
Starting new track at sector: 23395
Track 02:    0 of   45 MB written.
Track 02:    1 of   45 MB written (fifo 100%) [buf  96%]  12.8x.
Track 02:    2 of   45 MB written (fifo 100%) [buf  95%]  12.2x.
Track 02:    3 of   45 MB written (fifo 100%) [buf  98%]  12.7x.
Track 02:    4 of   45 MB written (fifo  98%) [buf 100%]  12.3x.
Track 02:    5 of   45 MB written (fifo 100%) [buf  97%]  12.6x.
Track 02:    6 of   45 MB written (fifo  98%) [buf  99%]  12.6x.
Track 02:    7 of   45 MB written (fifo  98%) [buf  99%]  12.7x.
Track 02:    8 of   45 MB written (fifo 100%) [buf  95%]  12.2x.
Track 02:    9 of   45 MB written (fifo 100%) [buf  98%]  12.6x.
Track 02:   10 of   45 MB written (fifo 100%) [buf  97%]  12.1x.
Track 02:   11 of   45 MB written (fifo 100%) [buf  97%]  12.6x.
Track 02:   12 of   45 MB written (fifo 100%) [buf  99%]  12.6x.
Track 02:   13 of   45 MB written (fifo 100%) [buf  99%]  12.6x.
Track 02:   14 of   45 MB written (fifo 100%) [buf  93%]  12.1x.
Track 02:   15 of   45 MB written (fifo 100%) [buf  98%]  12.6x.
Track 02:   16 of   45 MB written (fifo  98%) [buf  95%]  12.1x.
Track 02:   17 of   45 MB written (fifo 100%) [buf  95%]  12.6x.
Track 02:   18 of   45 MB written (fifo 100%) [buf  99%]  12.4x.
Track 02:   19 of   45 MB written (fifo 100%) [buf  97%]  12.2x.
Track 02:   20 of   45 MB written (fifo  98%) [buf  96%]  12.5x.
Track 02:   21 of   45 MB written (fifo 100%) [buf  98%]  12.6x.
Track 02:   22 of   45 MB written (fifo 100%) [buf  92%]  12.0x.
Track 02:   23 of   45 MB written (fifo 100%) [buf  97%]  12.5x.
Track 02:   24 of   45 MB written (fifo 100%) [buf  99%]  12.5x.
Track 02:   25 of   45 MB written (fifo 100%) [buf  97%]  12.0x.
Track 02:   26 of   45 MB written (fifo 100%) [buf  96%]  12.5x.
Track 02:   27 of   45 MB written (fifo 100%) [buf  98%]  12.5x.
Track 02:   28 of   45 MB written (fifo 100%) [buf  95%]  12.0x.
Track 02:   29 of   45 MB written (fifo 100%) [buf  98%]  12.5x.
Track 02:   30 of   45 MB written (fifo  98%) [buf  99%]  12.4x.
Track 02:   31 of   45 MB written (fifo 100%) [buf  97%]  12.0x.
Track 02:   32 of   45 MB written (fifo  98%) [buf  99%]  12.4x.
Track 02:   33 of   45 MB written (fifo 100%) [buf  99%]  12.5x.
Track 02:   34 of   45 MB written (fifo 100%) [buf  95%]  11.9x.
Track 02:   35 of   45 MB written (fifo 100%) [buf  95%]  12.5x.
Track 02:   36 of   45 MB written (fifo 100%) [buf 100%]  12.3x.
Track 02:   37 of   45 MB written (fifo 100%) [buf 100%]  12.4x.
Track 02:   38 of   45 MB written (fifo 100%) [buf  96%]  11.9x.
Track 02:   39 of   45 MB written (fifo 100%) [buf  99%]  12.4x.
Track 02:   40 of   45 MB written (fifo 100%) [buf  93%]  11.9x.
Track 02:   41 of   45 MB written (fifo 100%) [buf  98%]  12.4x.
Track 02:   42 of   45 MB written (fifo 100%) [buf  97%]  11.9x.
Track 02:   43 of   45 MB written (fifo 100%) [buf  96%]  12.2x.
Track 02:   44 of   45 MB written (fifo  98%) [buf  99%]  13.2x.
Track 02:   45 of   45 MB written (fifo 100%) [buf  96%]  12.2x.
Track 02: Total bytes read/written: 48145440/48145440 (20470 sectors).
Starting new track at sector: 43865
Track 03:    0 of   51 MB written.
Track 03:    1 of   51 MB written (fifo  98%) [buf 100%]  13.3x.
Track 03:    2 of   51 MB written (fifo 100%) [buf  99%]  12.2x.
Track 03:    3 of   51 MB written (fifo 100%) [buf  99%]  12.7x.
Track 03:    4 of   51 MB written (fifo 100%) [buf  93%]  12.2x.
Track 03:    5 of   51 MB written (fifo 100%) [buf  98%]  12.7x.
Track 03:    6 of   51 MB written (fifo 100%) [buf  97%]  12.2x.
Track 03:    7 of   51 MB written (fifo 100%) [buf  97%]  12.7x.
Track 03:    8 of   51 MB written (fifo 100%) [buf  99%]  12.6x.
Track 03:    9 of   51 MB written (fifo 100%) [buf  96%]  12.2x.
Track 03:   10 of   51 MB written (fifo 100%) [buf  98%]  12.6x.
Track 03:   11 of   51 MB written (fifo 100%) [buf  96%]  12.6x.
Track 03:   12 of   51 MB written (fifo 100%) [buf  97%]  12.1x.
Track 03:   13 of   51 MB written (fifo 100%) [buf  97%]  12.6x.
Track 03:   14 of   51 MB written (fifo 100%) [buf  99%]  12.6x.
Track 03:   15 of   51 MB written (fifo 100%) [buf  99%]  12.6x.
Track 03:   16 of   51 MB written (fifo 100%) [buf  93%]  12.1x.
Track 03:   17 of   51 MB written (fifo 100%) [buf  98%]  12.6x.
Track 03:   18 of   51 MB written (fifo 100%) [buf  95%]  12.1x.
Track 03:   19 of   51 MB written (fifo 100%) [buf  95%]  12.6x.
Track 03:   20 of   51 MB written (fifo 100%) [buf  97%]  12.0x.
Track 03:   21 of   51 MB written (fifo 100%) [buf  97%]  12.6x.
Track 03:   22 of   51 MB written (fifo 100%) [buf  98%]  12.5x.
Track 03:   23 of   51 MB written (fifo 100%) [buf  98%]  12.5x.
Track 03:   24 of   51 MB written (fifo 100%) [buf  98%]  12.0x.
Track 03:   25 of   51 MB written (fifo 100%) [buf  98%]  12.6x.
Track 03:   26 of   51 MB written (fifo  98%) [buf  99%]  12.4x.
Track 03:   27 of   51 MB written (fifo  98%) [buf  99%]  12.5x.
Track 03:   28 of   51 MB written (fifo 100%) [buf  96%]  12.0x.
Track 03:   29 of   51 MB written (fifo 100%) [buf  99%]  12.5x.
Track 03:   30 of   51 MB written (fifo 100%) [buf  95%]  12.0x.
Track 03:   31 of   51 MB written (fifo 100%) [buf  98%]  12.5x.
Track 03:   32 of   51 MB written (fifo 100%) [buf 100%]  12.0x.
Track 03:   33 of   51 MB written (fifo 100%) [buf  97%]  12.3x.
Track 03:   34 of   51 MB written (fifo  98%) [buf  99%]  12.4x.
Track 03:   35 of   51 MB written (fifo 100%) [buf  99%]  12.5x.
Track 03:   36 of   51 MB written (fifo 100%) [buf  95%]  11.9x.
Track 03:   37 of   51 MB written (fifo 100%) [buf  95%]  12.4x.
Track 03:   38 of   51 MB written (fifo 100%) [buf  97%]  11.9x.
Track 03:   39 of   51 MB written (fifo 100%) [buf  97%]  12.4x.
Track 03:   40 of   51 MB written (fifo 100%) [buf  99%]  12.3x.
Track 03:   41 of   51 MB written (fifo 100%) [buf  99%]  12.1x.
Track 03:   42 of   51 MB written (fifo  98%) [buf  98%]  12.2x.
Track 03:   43 of   51 MB written (fifo 100%) [buf  95%]  12.2x.
Track 03:   44 of   51 MB written (fifo 100%) [buf  97%]  12.7x.
Track 03:   45 of   51 MB written (fifo 100%) [buf  97%]  12.2x.
Track 03:   46 of   51 MB written (fifo 100%) [buf  97%]  12.7x.
Track 03:   47 of   51 MB written (fifo 100%) [buf  96%]  12.6x.
Track 03:   48 of   51 MB written (fifo  96%) [buf  96%]  12.6x.
Track 03:   49 of   51 MB written (fifo 100%) [buf  95%]  12.3x.
Track 03:   50 of   51 MB written (fifo 100%) [buf  92%]  12.7x.
Track 03:   51 of   51 MB written (fifo 100%) [buf  97%]  12.1x.
Track 03: Total bytes read/written: 54183024/54183024 (23037 sectors).
Starting new track at sector: 66902
Track 04:    0 of   46 MB written.
Track 04:    1 of   46 MB written (fifo  98%) [buf  99%]  12.3x.
Track 04:    2 of   46 MB written (fifo 100%) [buf  96%]  12.2x.
Track 04:    3 of   46 MB written (fifo 100%) [buf  96%]  12.7x.
Track 04:    4 of   46 MB written (fifo 100%) [buf  97%]  12.2x.
Track 04:    5 of   46 MB written (fifo 100%) [buf  97%]  12.7x.
Track 04:    6 of   46 MB written (fifo 100%) [buf  99%]  12.6x.
Track 04:    7 of   46 MB written (fifo 100%) [buf  99%]  12.7x.
Track 04:    8 of   46 MB written (fifo 100%) [buf  96%]  12.2x.
Track 04:    9 of   46 MB written (fifo 100%) [buf  96%]  12.7x.
Track 04:   10 of   46 MB written (fifo 100%) [buf  98%]  12.1x.
Track 04:   11 of   46 MB written (fifo 100%) [buf  95%]  12.6x.
Track 04:   12 of   46 MB written (fifo  98%) [buf  99%]  12.5x.
Track 04:   13 of   46 MB written (fifo  98%) [buf  99%]  12.6x.
Track 04:   14 of   46 MB written (fifo 100%) [buf  96%]  12.1x.
Track 04:   15 of   46 MB written (fifo 100%) [buf  99%]  12.6x.
Track 04:   16 of   46 MB written (fifo 100%) [buf  95%]  12.1x.
Track 04:   17 of   46 MB written (fifo 100%) [buf  98%]  12.5x.
Track 04:   18 of   46 MB written (fifo 100%) [buf 100%]  12.5x.
Track 04:   19 of   46 MB written (fifo 100%) [buf  97%]  12.1x.
Track 04:   20 of   46 MB written (fifo 100%) [buf  99%]  12.5x.
Track 04:   21 of   46 MB written (fifo 100%) [buf  94%]  12.6x.
Track 04:   22 of   46 MB written (fifo 100%) [buf  98%]  12.0x.
Track 04:   23 of   46 MB written (fifo 100%) [buf  98%]  12.6x.
Track 04:   24 of   46 MB written (fifo 100%) [buf  95%]  12.0x.
Track 04:   25 of   46 MB written (fifo 100%) [buf  97%]  12.5x.
Track 04:   26 of   46 MB written (fifo 100%) [buf  99%]  12.4x.
Track 04:   27 of   46 MB written (fifo 100%) [buf  96%]  12.0x.
Track 04:   28 of   46 MB written (fifo  98%) [buf  98%]  12.5x.
Track 04:   29 of   46 MB written (fifo 100%) [buf  98%]  12.5x.
Track 04:   30 of   46 MB written (fifo 100%) [buf  97%]  11.9x.
Track 04:   31 of   46 MB written (fifo 100%) [buf  97%]  12.5x.
Track 04:   32 of   46 MB written (fifo  98%) [buf  99%]  12.4x.
Track 04:   33 of   46 MB written (fifo  98%) [buf  99%]  12.5x.
Track 04:   34 of   46 MB written (fifo 100%) [buf  98%]  11.9x.
Track 04:   35 of   46 MB written (fifo 100%) [buf  98%]  12.5x.
Track 04:   36 of   46 MB written (fifo 100%) [buf  95%]  11.9x.
Track 04:   37 of   46 MB written (fifo 100%) [buf  95%]  12.4x.
Track 04:   38 of   46 MB written (fifo 100%) [buf  94%]  11.9x.
Track 04:   39 of   46 MB written (fifo 100%) [buf  97%]  12.4x.
Track 04:   40 of   46 MB written (fifo 100%) [buf  98%]  12.3x.
Track 04:   41 of   46 MB written (fifo 100%) [buf  98%]  12.4x.
Track 04:   42 of   46 MB written (fifo 100%) [buf  95%]  11.9x.
Track 04:   43 of   46 MB written (fifo 100%) [buf  99%]  12.6x.
Track 04:   44 of   46 MB written (fifo  98%) [buf  99%]  12.7x.
Track 04:   45 of   46 MB written (fifo 100%) [buf  99%]  12.2x.
Track 04:   46 of   46 MB written (fifo 100%) [buf  94%]  12.7x.
Track 04: Total bytes read/written: 49260288/49260288 (20944 sectors).
Starting new track at sector: 87846
Track 05:    0 of   44 MB written.
Track 05:    1 of   44 MB written (fifo 100%) [buf  97%]  12.5x.
Track 05:    2 of   44 MB written (fifo  98%) [buf  98%]  12.7x.
Track 05:    3 of   44 MB written (fifo 100%) [buf  96%]  12.7x.
Track 05:    4 of   44 MB written (fifo 100%) [buf  95%]  12.2x.
Track 05:    5 of   44 MB written (fifo 100%) [buf  95%]  12.7x.
Track 05:    6 of   44 MB written (fifo 100%) [buf  99%]  12.6x.
Track 05:    7 of   44 MB written (fifo 100%) [buf  99%]  12.7x.
Track 05:    8 of   44 MB written (fifo 100%) [buf  96%]  12.2x.
Track 05:    9 of   44 MB written (fifo 100%) [buf  96%]  12.7x.
Track 05:   10 of   44 MB written (fifo 100%) [buf  98%]  12.1x.
Track 05:   11 of   44 MB written (fifo 100%) [buf  95%]  12.7x.
Track 05:   12 of   44 MB written (fifo 100%) [buf  97%]  12.1x.
/usr/bin/X11/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 01 6C 8F 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F1 00 03 00 01 6A 1C 0A 00 2B 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 92700 (valid) 
resid: 63504
cmd finished after 5.305s timeout 200s
/usr/bin/X11/cdrecord: A write error occured.
/usr/bin/X11/cdrecord: Please properly read the error message above.
write track data: error after 12891312 bytes
Writing  time:  148.945s
Average write speed  28.5x.
Min drive buffer fill was 92%
Fixating...
Fixating time:    0.001s
BURN-Free was never needed.
/usr/bin/X11/cdrecord: fifo had 3523 puts and 3460 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 3138 times full, min fill was 87%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdb speed=24 -dao driveropts=burnfree -eject -useinfo -audio -shorttrack /tmp/kde-papa/k3b_audio_0_01.wav /tmp/kde-papa/k3b_audio_0_02.wav /tmp/kde-papa/k3b_audio_0_03.wav /tmp/kde-papa/k3b_audio_0_04.wav /tmp/kde-papa/k3b_audio_0_05.wav /tmp/kde-papa/k3b_audio_0_06.wav /tmp/kde-papa/k3b_audio_0_07.wav /tmp/kde-papa/k3b_audio_0_08.wav /tmp/kde-papa/k3b_audio_0_09.wav /tmp/kde-papa/k3b_audio_0_10.wav /tmp/kde-papa/k3b_audio_0_11.wav /tmp/kde-papa/k3b_audio_0_12.wav /tmp/kde-papa/k3b_audio_0_13.wav /tmp/kde-papa/k3b_audio_0_14.wav 

Just in case my fstab reads as follows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /media/windows  vfat rw,users,gid=users,umask=000, 0 0

Any help is welcome

THANKS ALL!!!!!  ):P

---

