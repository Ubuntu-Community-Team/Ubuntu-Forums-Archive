---
title: "Merlin x950D hspa express card problems"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by ken487 on 2009-04-08
Hi, I have a Merlin x950D express card.  I can't get it to work in Kubuntu 8.10.  

According the the manufacturer's instructions ([http://www.novatelwireless.com/index.php?option=com_content&view=article&id=176:linuxsetupumts&catid=43:linux-installation-instructions&Itemid=182]("http://www.novatelwireless.com/index.php?option=com_content&view=article&id=176:linuxsetupumts&catid=43:linux-installation-instructions&Itemid=182"))

it should be detected as a USB serial device (/dev/ttyUSB0) after pluging it in and doing the following:

sudo modprobe –r usbserial
sudo modprobe usbserial vendor=0x1410 product=0x4400

I do that, but no /dev/ttyUSB0 appears (or any other ttyUSB).

I did a tail on /var/log/messages after plugging it in and got this:

```
Apr  8 16:05:12 Cassini kernel: [101426.288145] usb 1-2: new full speed USB device using uhci_hcd and address 6
Apr  8 16:05:12 Cassini kernel: [101426.508998] usb 1-2: configuration #1 chosen from 1 choice
Apr  8 16:05:12 Cassini kernel: [101426.510661] scsi6 : SCSI emulation for USB Mass Storage devices
Apr  8 16:05:17 Cassini kernel: [101431.517237] scsi 6:0:0:0: CD-ROM            Novatel  Mass Storage     1.00 PQ: 0 ANSI: 2
Apr  8 16:05:17 Cassini kernel: [101431.560528] sr1: scsi-1 drive
Apr  8 16:05:17 Cassini kernel: [101431.562239] sr 6:0:0:0: Attached scsi generic sg2 type 5
Apr  8 16:05:17 Cassini kernel: [101431.776220] sr: Sense Key : No Sense [current]
Apr  8 16:05:17 Cassini kernel: [101431.776230] sr: Add. Sense: No additional sense information
```

It looks like it is being seen as a CDROM and not a serial modem.

Any ideas?

---

### Post by ken487 on 2009-04-11
I found the solution.  The x950d is indeed seen as a CD by the system.  That's because the card appears as a CD with a driver installer for windows users.  To use the card in linux, you have to unmount the CD first.  Then the card will be seen as a modem and you can connect using a ppp program as normal.

That crucial peice of info is missing from Novotel's Howto page.

---

### Post by tempooo on 2009-04-19
Hi ken ,
I run into the same problem with merlin x950D 
up untill the log i see exactly what you saw

e.g
Apr  8 16:05:12 Cassini kernel: [101426.288145] usb 1-2: new full speed USB device using uhci_hcd and address 6
Apr  8 16:05:12 Cassini kernel: [101426.508998] usb 1-2: configuration #1 chosen from 1 choice
Apr  8 16:05:12 Cassini kernel: [101426.510661] scsi6 : SCSI emulation for USB Mass Storage devices
Apr  8 16:05:17 Cassini kernel: [101431.517237] scsi 6:0:0:0: CD-ROM            Novatel  Mass Storage     1.00 PQ: 0 ANSI: 2
Apr  8 16:05:17 Cassini kernel: [101431.560528] sr1: scsi-1 drive
Apr  8 16:05:17 Cassini kernel: [101431.562239] sr 6:0:0:0: Attached scsi generic sg2 type 5
Apr  8 16:05:17 Cassini kernel: [101431.776220] sr: Sense Key : No Sense [current]
Apr  8 16:05:17 Cassini kernel: [101431.776230] sr: Add. Sense: No additional sense information

but i couldent repet the sulotion you sugested seens the CD cannot be unmounted(it is not mounted in the first place) .

Can you post a step by step instruction on the solution that worked for you with examples etc..

Thanks in advanced .

---

