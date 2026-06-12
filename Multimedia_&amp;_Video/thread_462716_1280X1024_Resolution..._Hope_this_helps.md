---
title: "1280X1024 Resolution... Hope this helps"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by rapollon on 2007-06-03
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?p=2765625#post2765625](http://ubuntuforums.org/showthread.php?p=2765625#post2765625) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I recently purchased a 19" lcd, problem was I was limited to 1024x768.  Monitor specs are: 1280x1024@75Hz, v:60.0-75.03/h:64.0-80.0

Even with these numbers dpkg-reconfigure as well as several hours of hit and miss edits of the xorg.conf did not work.  Determined to wipe the smiles off the virus infested microsoft "gurus" of my household I kept digging.

One resource [www.xfreee86.org](www.xfreee86.org) provided some useful documentation that actually made sense about the .conf file, each device has its own section and documentation.  

For laptop users, as in my case...  (using savage) xorg is creating the proper settings for your standard lcd screen.  Took a minute to click, I disabled to 15.4" and set the primary as the external from the bios.  Sho Nuf! the sucker worked and populated the correct resolution.

I hope this hopes, a third day of visine and coffee wasn't part of the plan!  off to bed!


My Hardware:

Processors	1
Model	Pentium III (Coppermine)
Chip MHz	701.63 MHz
Cache Size	256 KB
System Bogomips	1404.24
PCI Devices	0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE
0000:00:0c.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator
0000:00:0d.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100]
0000:00:0d.1 Serial controller: Xircom: Unknown device 00d3
0000:01:01.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV
0000:06:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
IDE Devices	hda: TOSHIBA MK1016GAP (Capacity: 9.37 GB)
hdc: DV-28E-A
SCSI Devices	Memorex 40EMAX 1240AJ (CD-ROM)
HP Photosmart 8400 (Direct-Access)
SanDisk U3 Cruzer Micro (Direct-Access)
SanDisk U3 Cruzer Micro (CD-ROM)
USB Devices	Linux 2.6.15-28-server uhci_hcd UHCI Host Controller 0000:00:07.2
SanDisk Corporation U3 Cruzer Micro 000017501B613989
USB2.0 -External USB20CD-RW CXR-2X40 1201E1F00008255B

---

