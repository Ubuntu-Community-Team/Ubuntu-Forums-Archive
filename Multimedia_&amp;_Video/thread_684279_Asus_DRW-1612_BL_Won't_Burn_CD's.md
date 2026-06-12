---
title: "Asus DRW-1612 BL Won't Burn CD's"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by Paul Vega on 2008-01-31
Kia Ora

I have an Asus DRW-1612 BL burner that will not complete a burn. It worked once but even then an error message came on saying that it didn't exit normally. Now it fails halfway through the process and says that it cannot mount the device. I have the following info if it helps:

 *-disk                  
       description: SCSI Disk
       product: ST340014A
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.10
       serial: 5JXBSYLH
       size: 37GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-cdrom
       description: DVD-RAM writer
       product: DRW-1612BL
       vendor: ASUS
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.04
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
  *-disk
       description: SCSI Disk
       product: DCP-130C
       vendor: Brother
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 1.00
       capabilities: removable
       configuration: ansiversion=2
     *-disc
          physical id: 0
          logical name: /dev/sdb

Can anyone help please?

Paul V

PS: How do you thank postee's? I have two previous posts and neither has been thanked although I thought that I had.

---

### Post by Craigus on 2008-02-01
Looks like a nice drive.

You need to exclude a hardware failure. Does the system boot into another other OS, or can you put the drive into another system and test it under another OS?

Another alternate is to use a linux live cd that has a "to RAM" option, so that you can boot, remove the CD and then test burning.

---

### Post by Paul Vega on 2008-02-01
Many Thanks Craigus

I do not have any MS on this PC. I purposefully stripped it all out before loading Ubuntu and I don't regret it at all. 

By the way I have been using K3b as my burning programe and as I have said, it worked the first time I used it but not since. It makes me wonder if my installation of the Brother DCP-130c last month may have hijacked some important setting. Any ideas out there?

Paul V

---

### Post by Paul Vega on 2008-02-09
Well, after buggering around for a while, I re-installed both Sound Juicer & Serpentine and I also installed some K3b Plug-ins and all seems to be working now.
Thanks anyway. Paul V

---

