---
title: "Hawking HWUN3 Wireless USB"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by A4orce84 on 2010-01-16
Anyone able to get this working in Ubuntu 9.10 ?

From what I researched its a relatively new wireless adapter, but it works on both Windows and Mac...so I thought maybe it would work on Linux too?

Thanks.


--Asif

---

### Post by pdc on 2010-01-17
well, what about plugging it in and typing 

> lsusb in a terminal and copying and pasting the result back here

and perhaps

> tail -f /var/log/messages

also

---

### Post by A4orce84 on 2010-01-17
lsusb:

asif@asif-desktop:~$ lsusb
Bus 002 Device 003: ID 03f0:1604 Hewlett-Packard DeskJet 940c
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0e66:0013 Hawking 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
asif@asif-desktop:~$ 



tail -f /var/log/messages :


asif@asif-desktop:~$ tail -f /var/log/messages 
Jan 17 20:30:35 asif-desktop kernel: [   15.460979] type=1505 audit(1263781835.314:21): operation="profile_replace" pid=1067 name=/usr/sbin/tcpdump
Jan 17 20:30:35 asif-desktop kernel: [   15.710291] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
Jan 17 20:30:35 asif-desktop kernel: [   15.750075] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:10.1/input/input5
Jan 17 20:30:35 asif-desktop kernel: [   15.969999] ppdev: user-space parallel port driver
Jan 17 20:30:37 asif-desktop kernel: [   17.474129] usb 2-4: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
Jan 17 20:30:46 asif-desktop kernel: [   26.503463] usplash:409 freeing invalid memtype fffffffffb000000-fffffffffbe00000
Jan 17 20:33:23 asif-desktop kernel: [  183.276999] sr0: CDROM not ready.  Make sure there is a disc in the drive.
Jan 17 20:38:45 asif-desktop kernel: [  505.820018] usb 1-5: new high speed USB device using ehci_hcd and address 4
Jan 17 20:38:45 asif-desktop kernel: [  505.987963] usb 1-5: configuration #1 chosen from 1 choice
Jan 17 20:38:56 asif-desktop kernel: [  516.561156] usb 2-4: usbfs: interface 0 claimed by usblp while 'usb' sets config #1


Let me know if there is anything else you need. Thanks.

--Asif

---

### Post by pdc on 2010-01-17
from this link, 

[http://www.linuxforums.org/forum/peripherals-hardware/149472-wireless-usb-adapter-hell.html](http://www.linuxforums.org/forum/peripherals-hardware/149472-wireless-usb-adapter-hell.html)

posts #2 and #3 talk of this having a Ralink

> RT2870 driver;

maybe a bit of google research by you and this link from the above may help

perhaps you re-post this as rt2870 driver help

---

### Post by m0rganic on 2010-11-09
This post worked for me on 9.10.

[http://ubuntuforums.org/showthread.php?t=1482145](http://ubuntuforums.org/showthread.php?t=1482145)

---

### Post by bkerrigan on 2010-12-09
> **m0rganic said:**
> This post worked for me on 9.10.

[http://ubuntuforums.org/showthread.php?t=1482145](http://ubuntuforums.org/showthread.php?t=1482145)

Same, it worked for me too and I am on 10.10.

---

