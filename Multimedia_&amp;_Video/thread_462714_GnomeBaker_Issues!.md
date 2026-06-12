---
title: "GnomeBaker Issues!"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by foxmulder881 on 2007-06-03
I am trying to erase a CD-RW disc using GnomeBaker and it doesn't seem to work. It outputs the following info:

```
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... giving up.
scsidev: 'ATA:/dev/hdc'
devname: 'ATA:/dev/hdc'
scsibus: -2 target: -2 lun: -2
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
TOC Type: 1 = CD-ROM
```

Why am I getting these errors? I have also tried using the Nautilus Burning Tool with the same errors. For the record, it's not the media I'm using as I have tried a DVD-RW also, to no avail.

---

### Post by foxmulder881 on 2007-06-03
C'mon guys. You're telling me no-one know this problem. Looks like I'll have to file a bug report at launchpad.net.

---

### Post by Majlo on 2007-06-04
Hi

Have you tried launching this command?
**cdrecord blank=fast**

I get this error too if i try format CD which is allready mounted .If i unmount CD before executing command it works.

[I]mario@server:~/Temp$ sudo cdrecord blank=fast
Password:
Quickly guessing the name of a drive capable to write CD-R, please wait...
Found /dev/cdrw, assuming dev=/dev/cdrw
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... giving up.
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.



mario@server:~/Temp$ sudo cdrecord blank=fast
Quickly guessing the name of a drive capable to write CD-R, please wait...
Found /dev/cdrw, assuming dev=/dev/cdrw
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-H42N '
Revision       : 'RL00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Speed set to 1764 KB/s
Starting to write CD/DVD at speed  10.0 in real BLANK mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.[/I]


In first case i tried format CD which were mounted .In second case CD was unmounted before executing .

---

### Post by foxmulder881 on 2007-06-05
You're 100% right Majlo. I get the same error if I attempt to erase while mounted.

I unmounted and then attempted another erase and it worked. And I got the same log results as you've posted above.

Why is it doing this? I previously run Edgy and Dapper releases and I never had this trouble.

---

