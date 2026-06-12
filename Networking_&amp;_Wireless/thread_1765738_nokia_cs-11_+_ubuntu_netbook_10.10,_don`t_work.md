---
title: "nokia cs-11 + ubuntu netbook 10.10, don`t work"
date: 2011-05-23
forum: Networking &amp; Wireless
---

### Post by thomazp on 2011-05-23
PLease,
My netbook with Ubuntu 10.10, don`t work with usb nokia cs-11 modem.
I read when the modem is detected as cdrom, it has only to eject the device to work, but I can`t find how to eject in UBUNTU 10.10 . When using 9.10, it was simple.

---

### Post by josephmills on 2011-05-23
Hi there could we please get some more info about the card make sure it is plugged in and open your terminal and type in ```
lsusb
``` and paste here thanks

---

### Post by thomazp on 2011-05-25
The modem is there:
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0421:061d Nokia Mobile Phones 
Bus 001 Device 003: ID eb1a:2761 eMPIA Technology, Inc. EeePC 701 integrated Webcam
Bus 001 Device 002: ID 0951:1606 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
And tail -f /var/log/messages
 tail -f /var/log/messages
May 25 21:21:35 thomaznetbook kernel: [ 2834.957058] scsi 4:0:0:0: CD-ROM            Nokia    Datacard CD-ROM  0001 PQ: 0 ANSI: 0
May 25 21:21:35 thomaznetbook kernel: [ 2834.966207] sr0: scsi3-mmc drive: 0x/0x caddy
May 25 21:21:35 thomaznetbook kernel: [ 2834.970965] sr 4:0:0:0: Attached scsi generic sg2 type 5
May 25 21:21:36 thomaznetbook kernel: [ 2835.276622] sr: Sense Key : Hardware Error [current] 
May 25 21:21:36 thomaznetbook kernel: [ 2835.276634] sr: Add. Sense: No additional sense information
May 25 21:21:37 thomaznetbook kernel: [ 2836.183521] sr: Sense Key : Hardware Error [current] 
May 25 21:21:37 thomaznetbook kernel: [ 2836.183533] sr: Add. Sense: No additional sense information
May 25 21:36:26 thomaznetbook kernel: [ 3725.377520] sr: Sense Key : Hardware Error [current] 
May 25 21:36:26 thomaznetbook kernel: [ 3725.377533] sr: Add. Sense: No additional sense information
May 25 21:36:26 thomaznetbook kernel: [ 3725.472663] usb 1-4: USB disconnect, address 5
I could't  find where to eject the cdrom, only found where to disconnect it.

---

### Post by tmowca on 2011-05-26
Same on ubuntu 11.04. Error with USB CD-ROM. Also usb_modeswitch command won't work.

---

### Post by us11csalyer on 2011-05-26
Im a noob so sorry if this is useless. Can you do unmount maybe?

---

