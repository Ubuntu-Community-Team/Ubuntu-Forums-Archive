---
title: "Burning CDs"
date: 2008-07-02
forum: Multimedia Software
---

### Post by Yaakov Stein on 2008-07-02
Hi-
Try as I may, I can't get my CD-RW working.I want to burn CDs but neither Banshee, Brasero, nor Grip will do anything.

The piece of hardware shows up in dmesg as: 
scsi0 : ata piix
scsi1 : ata piix
scsi 1:0:1:0: CD-ROM  HL-DT-ST CD-RW GCE-8400B, B104 PQ 0 ANSI: 5
scsi 1:0:1:0: Attached scsi generic sg3 type 5
sr   1:0:1:0: Attached scsi CD-ROM sr1

When I use the command cdrecord -scanbus   I get the following:
scsibus1:
      1,0,0  100) 'SAMSUNG ' 'DVD-ROM SD-616  ' 'F000' Removable CD-ROM
      1,1,0  101) 'HL-DT-ST' 'CD-RW GCE-8400B ' 'B104' Removable CD_ROM
      1,2,0  102) *
      1,3,0  103) *
      1,4,0  104) *
      1,5,0  105) *
      1,6,0  106) *
      1,7,0  107) *

I'm using Ubuntu 8.04
What should I do?

---

### Post by MrClearPore on 2008-07-03
According to your **cdrecord -scanbus** your CD burner is device **1,1,0** which means that when you're ready to burn your .iso image, you'll need to use

```
cdrecord dev=1,1,0 <file.iso>
```

Good luck!

---

### Post by thirstyghost on 2008-09-20
Try GnomeBaker.   I have Samsung burners too, and they both show up as Sony, and only on the one machine can I get it to *burn* disks by using GnomeBaker.   Otherwise they play disks great, but won't show up in burning menu choices.

---

