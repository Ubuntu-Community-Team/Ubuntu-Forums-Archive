---
title: "K3b problems - mic"
date: 2009-12-18
forum: Multimedia Software
---

### Post by AbdRahim on 2009-12-18
K3b worked fine in Jaunty. In Karmic when I start k3b it just stays busy. I tried to burn multi-session DVD's, but it could never import the session after the first was recorded. Need help

---

### Post by Danstroem on 2010-01-09
Hello,

I have the same problem while burning a CD-Extra (audio+data in two seperate sessions). The audio tracks are being burned and the session is closed, but k3b never seems to finish closing the session, or something like that. I tried to switch the writing app to cdrdao (option in k3b), but in this mode k3b dies with a segmentation fault. Only "auto" or "cdrecord" mode works. (In fact "auto" chooses cdrecord).

I have included the debugging output below. I already tried to add -eject into the user options of wodim/cdrecord, but it didn't help. The only thing to do is cancelling the burning process. The first (audio-)session nevertheless is correctly burned, only the second (data-)session is missing. Ubuntu Karmic (NOT studio), k3b 1.68.0~alpha3-0ub. There doesn't seem to be a different version of k3b available in synaptic.

Any hint greatly appreciated!

```

Devices
 -----------------------
 Optiarc DVD RW AD-7543A 1-00 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]
  K3b::IsoImager
 -----------------------
 mkisofs print size result: 74835 (153262080 bytes)
  System
 -----------------------
 K3b Version: 1.68.0
 KDE Version: 4.3.2 (KDE 4.3.2)
 QT Version:  4.5.2
 Kernel:      2.6.31-16-generic
  Used versions
 -----------------------
 mkisofs: 1.1.9
 cdrecord: 1.1.9
  cdrecord
 -----------------------
 /usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
 devname: '/dev/sr0'
 scsibus: -2 target: -2 lun: -2
 Linux sg driver version: 3.5.27
 Wodim version: 1.1.9
 SCSI buffer size: 64512
 Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
 communication breaks or freezes immediately after that.
 Text len: 666
 TOC Type: 0 = CD-DA
 Driveropts: 'burnfree'
 Device type    : Removable CD-ROM
 Version        : 5
 Response Format: 2
 Capabilities   : 
 Vendor_info    : 'Optiarc '
 Identification : 'DVD RW AD-7543A '
 Revision       : '1-00'
 Device seems to be: Generic mmc2 DVD-R/DVD-RW.
 Current: 0x0009 (CD-R)
 Profile: 0x002B (DVD+R/DL) 
 Profile: 0x001B (DVD+R) 
 Profile: 0x001A (DVD+RW) 
 Profile: 0x0016 (DVD-R/DL layer jump recording) 
 Profile: 0x0015 (DVD-R/DL sequential recording) 
 Profile: 0x0014 (DVD-RW sequential recording) 
 Profile: 0x0013 (DVD-RW restricted overwrite) 
 Profile: 0x0012 (DVD-RAM) 
 Profile: 0x0011 (DVD-R sequential recording) 
 Profile: 0x0010 (DVD-ROM) 
 Profile: 0x000A (CD-RW) 
 Profile: 0x0009 (CD-R) (current)
 Profile: 0x0008 (CD-ROM) (current)
 Profile: 0x0002 (Removable disk) 
 Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
 Driver flags   : MMC-3 SWABAUDIO BURNFREE 
 Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
 Drive buf size : 890880 = 870 KB
 FIFO size      : 12582912 = 12288 KB
 Speed set to 4234 KB/s
 pregap1: -1
 Track 01: audio   34 MB (03:26.85) no preemp swab copy
 Track 02: audio   46 MB (04:35.25) no preemp swab copy
 Track 03: audio   43 MB (04:18.57) no preemp swab copy
 Total size:      124 MB (12:20.68) = 55551 sectors
 Lout start:      124 MB (12:22/51) = 55551 sectors
 Current Secsize: 2048
 ATIP info from disk:
   Indicated writing power: 4
   Is not unrestricted
   Is not erasable
   Disk sub type: Medium Type A, low Beta category (A-) (2)
   ATIP start of lead in:  -12508 (97:15/17)
   ATIP start of lead out: 359845 (79:59/70)
 Disk type:    Short strategy type (Phthalocyanine or similar)
 Manuf. index: 22
 Manufacturer: Ritek Co.
 Blocks total: 359845 Blocks current: 359845 Blocks remaining: 304294
 Starting to write CD/DVD at speed  24.0 in real SAO mode for multi session.
 Last chance to quit, starting real write in    2 seconds.
    1 seconds.
    0 seconds. Operation starts.
 Waiting for reader process to fill input buffer ... input buffer ready.
 Performing OPC...
 Sending CUE sheet...
 SAO startsec: -12508
 Writing lead-in...
 Lead-in write time:   31.114s
 Writing pregap for track 1 at -150
 Starting new track at sector: 0
 Track 01:    0 of   34 MB written.
 Track 01:    1 of   34 MB written (fifo 100%) [buf 100%]  11.5x.
 Track 01:    2 of   34 MB written (fifo 100%) [buf 100%]   3.6x.
 Track 01:    3 of   34 MB written (fifo 100%) [buf 100%]   3.5x.

...

 Track 01:   31 of   34 MB written (fifo 100%) [buf 100%]  12.5x.
 Track 01:   32 of   34 MB written (fifo 100%) [buf 100%]   2.3x.
 Track 01:   33 of   34 MB written (fifo 100%) [buf 100%]  12.5x.
 Track 01:   34 of   34 MB written (fifo 100%) [buf 100%]  12.1x.
 Track 01: Total bytes read/written: 36488928/36488928 (15514 sectors).
 Starting new track at sector: 15514
 Track 02:    0 of   46 MB written.
 Track 02:    1 of   46 MB written (fifo 100%) [buf 100%]  12.6x.
 Track 02:    2 of   46 MB written (fifo 100%) [buf 100%]  12.5x.
 Track 02:    3 of   46 MB written (fifo 100%) [buf 100%]  12.9x.
 Track 02:    4 of   46 MB written (fifo 100%) [buf 100%]  12.5x.

...

 Track 02:   42 of   46 MB written (fifo 100%) [buf 100%]  13.2x.
 Track 02:   43 of   46 MB written (fifo 100%) [buf 100%]  13.6x.
 Track 02:   44 of   46 MB written (fifo 100%) [buf 100%]  14.1x.
 Track 02:   45 of   46 MB written (fifo 100%) [buf 100%]  13.6x.
 Track 02:   46 of   46 MB written (fifo 100%) [buf 100%]  14.0x.
 Track 02: Total bytes read/written: 48554688/48554688 (20644 sectors).
 Starting new track at sector: 36158
 Track 03:    0 of   43 MB written.
 Track 03:    1 of   43 MB written (fifo 100%) [buf 100%]  13.9x.
 Track 03:    2 of   43 MB written (fifo 100%) [buf 100%]  13.7x.
 Track 03:    3 of   43 MB written (fifo 100%) [buf 100%]  14.2x.

...

 Track 03:   40 of   43 MB written (fifo 100%) [buf 100%]  14.3x.
 Track 03:   41 of   43 MB written (fifo 100%) [buf 100%]  14.8x.
 Track 03:   42 of   43 MB written (fifo 100%) [buf 100%]  14.3x.
 Track 03:   43 of   43 MB written (fifo 100%) [buf 100%]  14.8x.
 Track 03: Total bytes read/written: 45612336/45612336 (19393 sectors).
 Writing  time:   94.994s
 Average write speed  11.6x.
 Min drive buffer fill was 100%
 Fixating...
 Fixating time:   21.168s
 /usr/bin/wodim: fifo had 2059 puts and 2059 gets.
 /usr/bin/wodim: fifo was 0 times empty and 1854 times full, min fill was 98%.
 BURN-Free was never needed.
  cdrecord command:
 -----------------------
 /usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=24 -sao driveropts=burnfree -multi textfile=/tmp/qt_temp.N22400 -useinfo -audio -pad -shorttrack /tmp/kde-daniel/k3b_audio_0_01.inf /tmp/kde-daniel/k3b_audio_0_02.inf /tmp/kde-daniel/k3b_audio_0_03.inf
  mkisofs
 -----------------------
 74835
  mkisofs calculate size command:
 -----------------------
 /usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid DespiseConquer -volset  -appid K3B THE CD KREATOR (C) 1998-2007 SEBASTIAN TRUEG -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-daniel/k3bc22400.tmp -rational-rock -hide-list /tmp/kde-daniel/k3bV22400.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-daniel/k3bH22400.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-daniel/k3br22400.tmp
 
```

---

