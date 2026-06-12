---
title: "Problems with 3G USB modem ZTE MF6273"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by darider on 2009-11-04
My system is a Thinkpad T500, I've upgraded to the latest Ubuntu 9.10. I've tried installing/using my 3g modem (ZTE MF6273 model) however have not been able to get it working. I believe I've setup everything correctly in "Network Connections", and the modem works properly under windows.

dmesg shows the following:

[30395.700142] usb 1-1: new high speed USB device using ehci_hcd and address 5
[30395.845547] usb 1-1: configuration #1 chosen from 1 choice
[30395.854164] scsi4 : SCSI emulation for USB Mass Storage devices
[30395.863120] usb-storage: device found at 5
[30395.863127] usb-storage: waiting for device to settle before scanning
[30400.861558] usb-storage: device scan complete
[30400.863671] scsi 4:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2

It seems to detect the modem and a storage device, and I can see a mount of it on my desktop. The files on this mount are the windows installation files for the modem.



Any hints or tips as to what I should be looking for changing will be greatly appreciated


Darider

---

### Post by pdc on 2009-11-04
when you say 

> I've upgraded to the latest Ubuntu 9.10

does that mean you have used Ubuntu before?

Some folks are having issues with mobile broadband on 9.10 when they did not have them on 9.04;

have you tried a google search on 

> ubuntu ZTE MF6273

also type 

> lsusb in a terminal with the modem plugged in and copy and paste the results back

---

