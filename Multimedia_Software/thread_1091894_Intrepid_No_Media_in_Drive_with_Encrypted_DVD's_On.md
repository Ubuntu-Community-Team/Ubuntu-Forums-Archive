---
title: "Intrepid: No Media in Drive with Encrypted DVD's Only, libdvdcss etc installed."
date: 2009-03-09
forum: Multimedia Software
---

### Post by MttJocy on 2009-03-09
I have a really strange problem, I can read unencrypted or data DVD's or CD's no problem, but as soon as I try with a commercial DVD it suddenly decides that there is no disk in the drive even running "lshw -C disk" seams to agree with this flawed assessment.

I have tried adding that all_generic_ide thing to my menu.lst file which was suggested in another thread about something similar and tried everything I could find re libdvdcss/dvdread but none of it seams to work.

So does anybody here have any ideas?

lshw -C disk (With DVD in drive)
  *-cdrom
       description: DVD writer
       product: DVDRW SOHW-1673S
       vendor: LITE-ON
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: JS01
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc

cdrecord -checkdrive dev=/dev/dvd (Also with DVD in drive)
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'LITE-ON '
Identification : 'DVDRW SOHW-1673S'
Revision       : 'JS01'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R

---

