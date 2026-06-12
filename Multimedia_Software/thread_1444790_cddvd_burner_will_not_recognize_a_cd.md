---
title: "cd/dvd burner will not recognize a cd"
date: 2010-04-01
forum: Multimedia Software
---

### Post by ewaynec on 2010-04-01
I have two optical drives, 1 a cd/dvd burner, 2 is a cd/dvd reader. 2 works as it should. 1 will read and write a dvd but will not read or write a cd. It did as late as one week ago, and I cannot remember doing anything during that time that might have affected it. 
  I have checked and tried some changes to fstab, no change, it is back to original. I have tried to manually mount with no success. I would appreciate some help. I have scoured the forums and did all the google searches I can think of. Here is the info on my disks.

sudo lshw -C disk
 
  *-cdrom:0               
       description: DVD writer
       product: DVD RW DW-D22A
       vendor: SONY
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: BFS1
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: DVD reader
       product: DVD-ROM GDR8163B
       vendor: HL-DT-ST
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 0S24
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: ATA Disk
       product: WDC WD5000AAKS-0
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WMASY0312355
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=c7b2d611
*-disk:0
       description: SCSI Disk
       product: UMH-U HS-MS
       vendor: Sony
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: 3.34
       serial: 3
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdb
  *-disk:1
       description: SCSI Disk
       product: UMH-U HS-CF
       vendor: Sony
       physical id: 0.0.1
       bus info: scsi@4:0.0.1
       logical name: /dev/sdc
       version: 3.34
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdc
  *-disk:2
       description: SCSI Disk
       product: UMH-U HS-XD
       vendor: Sony
       physical id: 0.0.2
       bus info: scsi@4:0.0.2
       logical name: /dev/sdd
       version: 3.34
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdd
  *-disk:3
 description: SCSI Disk
       product: UMH-U HS-SD/MMC
       vendor: Sony
       physical id: 0.0.3
       bus info: scsi@4:0.0.3
       logical name: /dev/sde
       version: 3.34
       capabilities: removable
     *-medium
          physical id: 0
          logi

---

### Post by ewaynec on 2010-04-11
If you happened to stumble upon this, just pick yourself up and go on. Like most of the other request for help it will pass on into oblivion unanswered.

---

### Post by the_overmaster on 2010-04-11
*-disk                  
       description: ATA Disk
       product: WDC WD1200JB-00E
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 15.0
       serial: WD-WCAEK1447014
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=bf74bf74
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM GSA-H55N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.05
       serial: [HL-DT-STDVD-RAM GSA-H55N1.0507/12/27 7U02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

Here's my DVD burner - and the same thing happens to me - except I don't know if it will read/write a CD - but it definitely will not read an audio CD (don't really have any Cds I could check with right now).  It will read Data DVDs.  I mean - wtf is going on?

---

### Post by yrhen on 2010-04-16
I can add my problem as well - 

 *-cdrom
       description: DVD-RAM writer
       product: CDDVDW TS-H653N
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: hb02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

or if I insert an empty 8.5 DL-DVD:
          configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

Except the bloody thing refuses to acknowledge that it actually should be able to write/burn anything, or even recognise an empty disk as something that could be written to. 
As no-one seems to respond to the previous authors it is either something extremely stupid or something extremely difficult....

---

### Post by yrhen on 2010-04-16
> **ewaynec said:**
> If you happened to stumble upon this, just pick yourself up and go on. Like most of the other request for help it will pass on into oblivion unanswered.
Maybe you could retitle the thread as "somebody help please"?:P

---

### Post by yrhen on 2010-04-16
or maybe it is related to this:
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/397806](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/397806) ?

---

### Post by Jive Turkey on 2010-04-16
> **yrhen said:**
> or maybe it is related to this:
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/397806](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/397806) ?

link is broken try [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397806]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397806")

---

### Post by yrhen on 2010-04-16
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397806](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397806)
ok. that was it - can't see the difference btw.

I very carefully followed the steps in the last post and .... tara!
the bloody thing works.
as always it's a pain in the ***, but mightily satisfying if one gets the machine running. thanks Vik :P

---

