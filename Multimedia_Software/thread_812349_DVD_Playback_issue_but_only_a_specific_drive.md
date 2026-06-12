---
title: "DVD Playback issue but only a specific drive"
date: 2008-05-29
forum: Multimedia Software
---

### Post by Norst on 2008-05-29
I just installed a LG Drive (BDDVDRW GGC-H20L), it's a blu-Ray/HD-DVD/DVD-R/W drive with Light Scribe. It is connected to a SATA 2-port pci card I had to add, due to my on-board SATA being full (it is the only SATA CD device I have, all the other CD drives are IDE). Everything seems to get detected just fine.

```
*-storage:0
                description: RAID bus controller
                product: SiI 3512 [SATALink/SATARaid] Serial ATA Controller
                vendor: Silicon Image, Inc.
                physical id: 1
                bus info: pci@0000:01:01.0
                logical name: scsi2
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: storage pm bus_master cap_list emulated
                configuration: driver=sata_sil latency=64 module=sata_sil
              *-cdrom
                   description: DVD-RAM writer
                   product: BDDVDRW GGC-H20L
                   vendor: HL-DT-ST
                   physical id: 0.0.0
                   bus info: scsi@2:0.0.0
                   logical name: /dev/cdrom2
                   logical name: /dev/dvd2
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   logical name: /media/cdrom0
                   version: 1.02
                   capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
                 *-medium
                      physical id: 0
                      logical name: /dev/cdrom2
                      logical name: /media/cdrom0
                      configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted
```

Yet for some reason it's picky about what it does. I can read DVD-R/CD/DVD-R/W, but if I try to play a movie in it, I either get a totem lockup, or junky vid in mplayer with no audio (looks like scrolling lego, no decipherable images of any kind). I can browse the contents of the dvd, but it won't even generate thumbnails when viewing .vob files in a directory. 

At first I thought it might be a region code setting, but running:

```
 regionset /dev/dvd2 
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE

```

Tells, me that is fine because Region 1 is what I want. It would seem the only thing left would have to be DeCSS related. I have reinstalled libdvdcss2 but to no avail. I can play DVDs just fine in my other DVD drive (IDE). Any help would be great.

Norst

---

### Post by browneej on 2008-05-30
I have a sony blu-ray IDE drive, but it demonstrates the same problem.  It took me a while to diagnose it to the drive vs software problems.  Swapping it with a DVD-ROM fixed all my problems.

Also, the blu-ray will not load up either the live or alternate 8.04 disks in my experience.  Had to install with the DVD-ROM. 

I have no answers yet.  If you figure something out let me know.

---

