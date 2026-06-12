---
title: "K3b won't burn"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by Verplrke on 2007-04-24
I'm running kubuntu 7.04 Feisty Fawn with kernel v2.6.20-15-386 (updated from Kubuntu 6.10 Edgy).

I'm having trouble burning stuff in K3b. I didn't try burning something when I was still running 6.10 so I wouldn't know if it worked then. To avoid any permission problems I started K3b as root. I've also updated K3b to the latest 1.0.1 version.

When burning a DVD+RW it gives an error during the erasing of the (empty) disc. And debug shows this:
```
System
-----------------------
K3b Version: 1.0.1

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-15-386
Devices
-----------------------
MATSHITA DVD-RAM UJ-820S 1.50 (/dev/hdc, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW] [DVD-ROM, DVD-R sequential, DVD-RAM, DVD-RW with restricted overwrite, DVD-RW sequential, DVD+RW, DVD+R, CD-ROM, CD-R, CD-RW] [SAO, TAO, restricted overwrite]


```

When trying to erase a CD-RW this is the debug:
```
System
-----------------------
K3b Version: 1.0.1

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-15-386
Devices
-----------------------
MATSHITA DVD-RAM UJ-820S 1.50 (/dev/hdc, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW] [DVD-ROM, DVD-R sequentieel, DVD-RAM, DVD-RW met beperkte overschrijving, DVD-RW sequentieel, DVD+RW, DVD+R, CD-ROM, CD-R, CD-RW] [SAO, TAO, Beperkt overschrijven]

Used versions
-----------------------
cdrecord: 1.1.2

cdrecord command:
-----------------------
/usr/bin/X11/wodim -v gracetime=2 dev=/dev/hdc speed=8 -tao driveropts=burnfree -eject blank=fast -force 

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
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identification : 'DVD-RAM UJ-820S '
Revision       : '1.50'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A (CD-RW)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) (current)
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) (current)
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO
Drive buf size : 1310720 = 1280 KB
Speed set to 1411 KB/s
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 1
  Reference speed: 0
  Is not unrestricted
  Is erasable
  Disk sub type: Ultra High speed Rewritable media (2)
  ATIP start of lead in:  -11633 (97:26/67)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low: 16 1T speed high: 16
  2T speed low:  8 2T speed high: 24
  power mult factor: 4 5
  recommended erase/write power: 2
  A1 values: 66 4A A5
  A2 values: 38 80 00
  A3 values: 04 C9 90
Disk type:    Phase change
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Waiting for drive to calm down.
Starting to write CD/DVD at speed   8.0 in real force BLANK mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Starting to write CD/DVD at speed   8.0 in real force BLANK mode for single session.
No chance to quit anymore. Operation starts.
Errno: 0 (Success), blank unit scsi sendcmd: no error
CDB:  A1 01 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 9600s
Performing OPC...
Blanking PMA, TOC, pregap
Errno: 0 (Success), blank unit scsi sendcmd: no error
CDB:  A1 01 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 9600s
/usr/bin/X11/wodim: Cannot blank disk, aborting.
/usr/bin/X11/wodim: Some drives do not support all blank types.
/usr/bin/X11/wodim: Try again with wodim blank=all.

```

---

