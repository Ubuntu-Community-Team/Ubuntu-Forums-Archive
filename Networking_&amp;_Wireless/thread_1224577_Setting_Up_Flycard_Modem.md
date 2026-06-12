---
title: "Setting Up Flycard Modem"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by axeblade346 on 2009-07-27
Hi.
I have a Problem setting up my FlyCard Fly-H1_a  3g USB Modem under Linux Ubuntu 9.04.

It looks like it only detects it as a CD-Rom and i do not know how to tell it its a Modem.
on the back of the modems box it says it supports linux but [www.fly-card.com]("http://www.fly-card.com") has been under contrusction for the last 3 weeks.
Please note I know C++ Programing but am a little new to linux.


In the Code is all the info i could get you guys - hope it helps.

```


From SYSTEM LOG VIEWER -> MESSAGES

Jul 19 17:02:19 axe346-desktop kernel: [  232.677638] usb 1-3.4: USB disconnect, address 8
Jul 19 17:02:25 axe346-desktop kernel: [  238.508374] usb 1-3.4: new high speed USB device using ehci_hcd and address 12
Jul 19 17:02:25 axe346-desktop kernel: [  238.603686] usb 1-3.4: configuration #1 chosen from 1 choice
Jul 19 17:02:25 axe346-desktop kernel: [  238.605593] scsi9 : SCSI emulation for USB Mass Storage devices
Jul 19 17:02:30 axe346-desktop kernel: [  243.605464] scsi 9:0:0:0: CD-ROM            USBModem Disk             2.31 PQ: 0 ANSI: 2
Jul 19 17:02:30 axe346-desktop kernel: [  243.608417] sr1: scsi-1 drive
Jul 19 17:02:30 axe346-desktop kernel: [  243.608602] sr 9:0:0:0: Attached scsi generic sg3 type 5

AND SYSTEM LOG
Jul 19 17:02:19 axe346-desktop kernel: [  232.677638] usb 1-3.4: USB disconnect, address 8
Jul 19 17:02:25 axe346-desktop kernel: [  238.508374] usb 1-3.4: new high speed USB device using ehci_hcd and address 12
Jul 19 17:02:25 axe346-desktop kernel: [  238.603686] usb 1-3.4: configuration #1 chosen from 1 choice
Jul 19 17:02:25 axe346-desktop kernel: [  238.605593] scsi9 : SCSI emulation for USB Mass Storage devices
Jul 19 17:02:25 axe346-desktop kernel: [  238.605670] usb-storage: device found at 12
Jul 19 17:02:25 axe346-desktop kernel: [  238.605677] usb-storage: waiting for device to settle before scanning
Jul 19 17:02:30 axe346-desktop kernel: [  243.604625] usb-storage: device scan complete
Jul 19 17:02:30 axe346-desktop kernel: [  243.605464] scsi 9:0:0:0: CD-ROM            USBModem Disk             2.31 PQ: 0 ANSI: 2
Jul 19 17:02:30 axe346-desktop kernel: [  243.608417] sr1: scsi-1 drive
Jul 19 17:02:30 axe346-desktop kernel: [  243.608514] sr 9:0:0:0: Attached scsi CD-ROM sr1
Jul 19 17:02:30 axe346-desktop kernel: [  243.608602] sr 9:0:0:0: Attached scsi generic sg3 type 5
Jul 19 17:02:33 axe346-desktop kernel: [  246.059801] ISO 9660 Extensions: Microsoft Joliet Level 3
Jul 19 17:02:33 axe346-desktop kernel: [  246.061295] ISOFS: changing to secondary root
Jul 19 17:02:33 axe346-desktop hald: mounted /dev/sr1 on behalf of uid 1000

IT IS MOUNTED IN /MEDIA/MODEM

AND IN DEBUG
Jul 19 16:58:41 axe346-desktop kernel: [   12.488209] usb-storage: device scan complete
Jul 19 16:58:41 axe346-desktop kernel: [   12.545307] sd 8:0:0:0: [sdb] Mode Sense: 34 00 00 00
Jul 19 16:58:41 axe346-desktop kernel: [   12.546680] sd 8:0:0:0: [sdb] Mode Sense: 34 00 00 00
Jul 19 16:58:48 axe346-desktop kernel: [   20.873033] atl1 0000:02:00.0: irq 2299 for MSI/MSI-X
Jul 19 16:58:55 axe346-desktop kernel: [   28.403887] ISO 9660 Extensions: Microsoft Joliet Level 3
Jul 19 16:58:55 axe346-desktop kernel: [   28.404547] ISOFS: changing to secondary root
Jul 19 16:59:02 axe346-desktop kernel: [   35.328007] eth0: no IPv6 routers present
Jul 19 17:02:25 axe346-desktop kernel: [  238.605670] usb-storage: device found at 12
Jul 19 17:02:25 axe346-desktop kernel: [  238.605677] usb-storage: waiting for device to settle before scanning
Jul 19 17:02:30 axe346-desktop kernel: [  243.604625] usb-storage: device scan complete
Jul 19 17:02:30 axe346-desktop kernel: [  243.608514] sr 9:0:0:0: Attached scsi CD-ROM sr1
Jul 19 17:02:33 axe346-desktop kernel: [  246.059801] ISO 9660 Extensions: Microsoft Joliet Level 3
Jul 19 17:02:33 axe346-desktop kernel: [  246.061295] ISOFS: changing to secondary root


```The Modem installs the same way as an e220 modem in XP- First as a flashdrive,then CD-ROM then as a DataCard.

I do not know what chipset it uses.

---

