---
title: "DVD Drive Will Not recognise DVDs"
date: 2011-04-13
forum: Multimedia Software
---

### Post by Jack Bonner on 2011-04-13
I'm usually an Arch Linux Fellow so I have little experience with Debian based systems. I'm installing Ubuntu 10.10 on this laptop for my mum, everything works fine apart from the DVD drive. It refuses to detect DVDs at all (I've tried 8 different ones). It grinds and grumbles at me and makes all sorts of ungodly noises. The drive works fine mechanically as it's been used before under Arch and I used it to install Ubuntu yesterday. I've installed all the relevant codec packages and other odds and ends to play DVDs with, but still nothing.

Anyone got any ideas? I'm stumped!


Sudo lshw -c disk output:

```


*-cdrom                 
       description: DVD-RAM writer
       product: DVDRAM GSA-T20L
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: NC08
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: ATA Disk
       product: FUJITSU MHY2080B
       vendor: Fujitsu
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 890B
       serial: K40YT7B2632M
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000c229e

```

---

### Post by Jack Bonner on 2011-04-13
Just an update;

The drive will recognise and work with normal CDs and also CD-ROMs, but it won't touch DVDs.

---

