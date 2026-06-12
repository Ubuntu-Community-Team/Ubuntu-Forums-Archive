---
title: "mp3 player not detected"
date: 2011-06-15
forum: Multimedia Software
---

### Post by petibor on 2011-06-15
Just got a new mp3 player that does not appear to be detected, seems to have trouble mounting. It tries to go in USB transfer mode but then just goes into charge mode.
I run on ubuntu 11.04.


here is a print of the last lines of dmesg just after i plug in the mp3 player:


```
[21793.150092] usb 1-7: new high speed USB device using ehci_hcd and address 18
[21793.308537] usb-storage 1-7:1.0: Quirks match for vid 071b pid 3203: 80600
[21793.308624] scsi15 : usb-storage 1-7:1.0
[21794.302323] scsi 15:0:0:0: Direct-Access     HiFiMAN  USBDISK  User    1.00 PQ: 0 ANSI: 0
[21794.302789] scsi 15:0:0:1: Direct-Access     HiFiMAN  USBDISK    SD    1.00 PQ: 0 ANSI: 0
[21794.310834] sd 15:0:0:0: Attached scsi generic sg2 type 0
[21794.311329] sd 15:0:0:1: Attached scsi generic sg3 type 0
[21794.313209] sd 15:0:0:0: [sdb] 16023552 512-byte logical blocks: (8.20 GB/7.64 GiB)
[21794.313220] sd 15:0:0:0: [sdb] Assuming Write Enabled
[21794.430056] usb 1-7: reset high speed USB device using ehci_hcd and address 18
[21809.550040] usb 1-7: device descriptor read/64, error -110
[21824.780070] usb 1-7: device descriptor read/64, error -110
[21825.010054] usb 1-7: reset high speed USB device using ehci_hcd and address 18
[21825.160088] usb 1-7: USB disconnect, address 18
[21825.160519] sd 15:0:0:0: Device offlined - not ready after error recovery
[21825.161236] sd 15:0:0:1: [sdc] Attached SCSI removable disk
[21825.161267] sd 15:0:0:0: [sdb] No Caching mode page present
[21825.161274] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[21825.161682] sd 15:0:0:0: [sdb] Attached SCSI removable disk

```Some threads recommended to try :

sudo rmmod ehci_hcd

but the command is not recongnized.

Any ideas?

---

### Post by petibor on 2011-06-15
solved updating kernel 

see

[http://ubuntuforums.org/showthread.php?t=1778441&page=2](http://ubuntuforums.org/showthread.php?t=1778441&page=2)

---

