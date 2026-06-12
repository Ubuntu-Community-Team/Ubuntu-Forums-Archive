---
title: "SATA Disk Errors and IVTV Buffer Full Errors"
date: 2008-04-16
forum: Mythbuntu
---

### Post by wd5iyt on 2008-04-16
I've recently switched my mythtv systems to mythbuntu from Fedora 4 using Jarod Wilson's "standard configuration".

This hardware has been running fine with FC4 and Myth .20-2 for several years with no issues.

While running 8.04 Beta, I'm seeing lots of SATA related disk errors.  For example:

> Apr 16 08:00:59 mythbackend kernel: [136851.532709]          res 51/40:00:48:36:56/40:00:04:00:00/e1 Emask 0x9 (media error)
Apr 16 08:00:59 mythbackend kernel: [136851.668754] ata1.00: configured for UDMA/133
Apr 16 08:00:59 mythbackend kernel: [136851.668770] ata1: EH complete
Apr 16 08:00:59 mythbackend kernel: [136855.905699]          res 51/40:00:4d:36:56/40:00:04:00:00/e1 Emask 0x9 (media error)
Apr 16 08:00:59 mythbackend kernel: [136855.927520] ata1.00: configured for UDMA/133
Apr 16 08:00:59 mythbackend kernel: [136855.927538] ata1: EH complete

I'm also seeing at the same time IVTV errors:

> Apr 16 08:00:59 mythbackend kernel: [136856.302185] ivtv0: All encoder MPG stream buffers are full. Dropping data.
Apr 16 08:00:59 mythbackend kernel: [136856.302192] ivtv0: Cause: the application is not reading fast enough.

This is a Gigabyte Intel motherboard with a PCI Express video card, a single PVR-150 and a 500 GB SATA drive.

I never had any hardware issues with this system running the previous OS and mythtv versions, so I'm reluctant to think this is hardware, but I wouldn't rule it out completely.

It sure looks like a PCI issue.  Perhaps Ubuntu handles that differently?

Anyone seeing similar issues?  I'm pretty familiar with Ubuntu and mythtv, but I've not encountered anything like this.  It is causing data corruption on the drive.  Every couple of days I have to fsck to fix the filesystem.

I'm using LVM on the video partition.

I admit, this one has me stumped.

---

### Post by ian dobson on 2008-04-16
Hi,

Sounds more like your harddisk is dieing. On my raid5 array with 4x500Gb WD drives I got alot of similar error messages before one of the drives died.

Try just copying afew large files around and see if the errors are still comming up without recording anything.

Regards
Ian Dobson

---

### Post by wd5iyt on 2008-04-18
Yes, unfortunately it was just a coincidence.  After a couple of days with random errors, the drive hard failed.  

You would think that after all this time playing with computers I would have learned to always check the hardware first!  :)

I'm now running fine with a new drive...false alarm.

---

