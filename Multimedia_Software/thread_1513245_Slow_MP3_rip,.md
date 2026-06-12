---
title: "Slow MP3 rip,"
date: 2010-06-19
forum: Multimedia Software
---

### Post by Dave Reynolds on 2010-06-19
I've recently tried switching from Windows (7) to Ubuntu 10.04 (dual boot) on a couple of machines  (amd64 arch) and each shows the same problem.

The problem is slowness of ripping audio CDs to MP3 format. I'm mostly  using Rythmbox having installed ubuntu-restricted-extras but have also  tried other programs such as RubyRipper and RipOff. I'm getting an  encoding speed of around 2x which is ... slow.

Looking around I see a common piece of advice is that DMA might not be  configured properly for the drive but the dmesg log looks OK:

 	Code:
 	[    2.093671] ata2.00: ATAPI: Optiarc DVD RW AD-7201S5, 1H0E, max UDMA/100
[    2.095135] ata2.00: configured for UDMA/100
[    2.121566] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7201S5 1H0E PQ: 0 ANSI: 5
[    2.122798] usb 2-5.2: new high speed USB device using ehci_hcd and address 6
[    2.126185] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.126189] Uniform CD-ROM driver Revision: 3.20
[    2.126298] sr 1:0:0:0: Attached scsi CD-ROM sr0 
The interesting diagnostic is how this affects Windows ...

If I boot into Ubuntu, try a rip I get 1.7x. If I then restart (no power  down) and boot into Windows 7 and try Windows Media Player to do the  same rip I get about 4x. That is better than Ubuntu but still  pathetically slow for windows.  If I power down and then boot cleanly  into Windows the same rip from the same CD with the same software and  settings gives 20x which is much more like normal speeds.

Somehow the process of trying to Rip from Ubuntu leaves the drive in a  state which prevents fast rips.

Any suggestions both on what might be preventing fast rips on Lucid Lynx  and on what it is doing to the DVD drive that is sticky across  non-power-down reboots?

Cheers,
Dave

---

