---
title: "Can't enable broadcom wireless card..."
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by Barbellion on 2010-09-28
I've installed Ubuntu 10.04.1 LTS on my AMD64 architecture laptop, but I can't get my wireless to work - it's status is stuck on "disabled" and I can't enable it.
 
(Chipset BCM4312 802.11b/g , PCI-ID 14e4:4315)
 
I've been struggling my way through this and I've found the page 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
which appears to outline the solution I need, only (having installed from CD) I can't add cd rom to my synaptic manager to install [FONT=Courier New][COLOR=black]bcmwl-kernel-source[/COLOR][/FONT] as asked (although I can open the CD itself, package manager doesn't recognise the install disk). 
 
- I've tried to browse to the file in the cd-rom, but there are no files shown in the pool folder of the disk I installed from (even viewing hidden files).
 
- I've tried installing [COLOR=black]b43-fwcutter_011-1_amd64 [FONT=Arial]from usb, but it tries to connect to internet to wget something which it fails at (because I'm not online on that computer...).[/FONT][/COLOR]

[FONT=Arial]So I'm at quite a loss - I'm not Ubuntu savvy (being new and all...) so I don't know how to work this through. Anyone have any advice? About getting the CD to mount, or doing this some other way? [/FONT]

[FONT=Arial]Can't do anything much with my laptop till it's online :([/FONT]

---

### Post by bkratz on 2010-09-28
That particular ID ( PCI-ID 14e4:4315) on this page 
[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)  says the following regarding the b43 driver:

14e4:4315
partially supported 2.6.33 and later (PIO mode)
BCM4312

10.04 is in the 2.6.32 kernel range so you probably have to try the STA driver.

This thread in post 19 points at how to do the install from the CD for 64 bits.
[http://ubuntuforums.org/showthread.php?t=1578443&page=2](http://ubuntuforums.org/showthread.php?t=1578443&page=2)

Good luck!

---

