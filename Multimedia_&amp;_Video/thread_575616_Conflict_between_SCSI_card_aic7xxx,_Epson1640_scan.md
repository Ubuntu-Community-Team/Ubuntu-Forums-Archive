---
title: "Conflict between SCSI card aic7xxx, Epson1640 scanner and Terratec BT8xx TV card"
date: 2007-10-14
forum: Multimedia &amp; Video
---

### Post by e-paul on 2007-10-14
I am experiencing a conflict between my SCSI card (aic7xxx) and my TV card (Terratec BT8xxx). My Ubuntu version is Kubuntu Feisty Fawn 7.04.

Xsane just wont't find the scanner (EPSON 1640) when the TV card is installed in the PC.

Sane-find-scanner will just say that no SCSi scanner was detected. If I start xsane anyway, I'll get the usual xsane window, but the settings and the infos about the scanner refer to the TV card.

If I remove the TV card the scanner will work OK.

I had the same problem with Ubuntu Dapper, but it was resolved magically during some system upgrade, and the scanner begun working flawlessly. When I started xsane, I was given a choice between the two input sources (Terratec BT878 tv card / Epson 1640 scanner)
Anyway I always had to issue the following commends when I had to turn on the scanner:
modprobe sg
modprobe -r aic7xxx
modprobe aic7xxx
chown root.scanner /dev/sgxx (xx=scanner device number)

At the moment the scanner seem to be somehow recognized anyway, tough it won't work
paolo@bigblackbear:~$ dmesg | grep scsi
[   63.156587] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   63.158472] scsi1 : sata_via
[   63.560666] scsi2 : sata_via
[   63.960337] scsi: waiting for bus probes to complete ...
[   64.994928] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 7Y250M0   YAR5 PQ: 0 ANSI: 5
[   64.995481] scsi 2:0:0:0: Direct-Access     ATA      MAXTOR STM325031 3.AA PQ: 0 ANSI: 5
[   65.038412] sd 1:0:0:0: Attached scsi disk sda
[   65.062193] sd 2:0:0:0: Attached scsi disk sdb
[   65.066558] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   65.066696] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   67.489812] scsi3 : sata_promise
[   67.801471] scsi4 : sata_promise
[   68.113255] scsi5 : sata_promise
[   81.207335] scsi6 : SCSI emulation for USB Mass Storage devices
[   86.205663] scsi 6:0:0:0: Direct-Access     HP       Photosmart D5100 1.00 PQ: 0 ANSI: 2
[   86.206805] sd 6:0:0:0: Attached scsi removable disk sdc
[   86.206841] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 9272.820000] scsi0: Someone reset channel A
[ 9307.248000] scsi7 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[ 9307.784000] scsi 7:0:2:0: Processor         EPSON    Perfection1640   1.04 PQ: 0 ANSI: 2
[ 9308.844000] scsi 7:0:2:0: Attached scsi generic sg3 type 3

Any help?
Thanks
Paolo

---

