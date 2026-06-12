---
title: "Sprint Air Card not found on Karmic?"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by RX8volution on 2009-11-09
Hi, just re-loaded this laptop with the new 9.10 ISO and everything looks great EXCEPT the fact that I can't get WLAN to connect ...

When I plug in my Sprint Ovation U727, dmesg shows:

[  965.956157] usb 7-1: new full speed USB device using uhci_hcd and address 2
[  966.112595] usb 7-1: configuration #1 chosen from 1 choice
[  966.115708] scsi7 : SCSI emulation for USB Mass Storage devices
[  966.116643] usb-storage: device found at 2
[  966.116648] usb-storage: waiting for device to settle before scanning
[  971.118026] usb-storage: device scan complete
[  971.120964] scsi 7:0:0:0: CD-ROM            Novatel  Mass Storage     1.00 PQ: 0 ANSI: 2
[  971.149928] sr1: scsi-1 drive
[  971.150156] sr 7:0:0:0: Attached scsi CD-ROM sr1
[  971.150286] sr 7:0:0:0: Attached scsi generic sg2 type 5
[  971.386053] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[  971.386085] sr: Sense Key : No Sense [current] 
[  971.386094] sr: Add. Sense: No additional sense information
[  971.450117] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[  971.450148] sr: Sense Key : No Sense [current] 
[  971.450157] sr: Add. Sense: No additional sense information
[  971.461350] sr 7:0:0:0: [sr1] unaligned transfer
[  971.464122] sr 7:0:0:0: [sr1] unaligned transfer
[  971.652217] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[  971.652246] sr: Sense Key : No Sense [current] 
[  971.652256] sr: Add. Sense: No additional sense information
[  971.676214] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[  971.676241] sr: Sense Key : No Sense [current] 
[  971.676250] sr: Add. Sense: No additional sense information


Anyone have any hints here?  Is this a bug?  Has anyone set up a Sprint mobile broadband card they can share?

Thanks in advance.

---

### Post by RX8volution on 2009-11-09
OK ... so a little more Google'ing found me this site ([http://ubuntuforums.org/showthread.php?t=677676]("http://ubuntuforums.org/showthread.php?t=677676")), and I've now got the connection manager to "see" the WLAN card - but sadly I have NO IDEA what the userID and password here it's asking for is.  In my old Windows-based laptop (*ducks*) I just plugged it in and the Sprint software just "worked" ... thoughts?

Thanks.

---

