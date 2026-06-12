---
title: "ipod wont mount (dapper drake)"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by netron on 2007-04-21
i just got a new ipod nano and it wont mount on my dapper drake laptop (i just havent got around to upgrading to feisty just yet)

the odd thing is , is that it shows up in dmesg just fine.

> 
[17180546.800000] Initializing USB Mass Storage driver...
[17180546.800000] scsi0 : SCSI emulation for USB Mass Storage devices
[17180546.800000] usb-storage: device found at 2
[17180546.800000] usb-storage: waiting for device to settle before scanning
[17180546.800000] usbcore: registered new driver usb-storage
[17180546.800000] USB Mass Storage support registered.
[17180551.800000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17180551.800000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17180551.820000] usb-storage: device scan complete
[17180552.084000] Driver 'sd' needs updating - please use bus_type methods
[17180552.088000] SCSI device sda: 1982464 2048-byte hdwr sectors (4060 MB)
[17180552.088000] sda: Write Protect is off
[17180552.088000] sda: Mode Sense: 68 00 00 08
[17180552.088000] sda: assuming drive cache: write through
[17180552.092000] SCSI device sda: 1982464 2048-byte hdwr sectors (4060 MB)
[17180552.096000] sda: Write Protect is off
[17180552.096000] sda: Mode Sense: 68 00 00 08
[17180552.096000] sda: assuming drive cache: write through
[17180552.096000]  sda: sda1 sda2
[17180552.100000] sd 0:0:0:0: Attached scsi removable disk sda
[17180552.168000] sd 0:0:0:0: Attached scsi generic sg0 type 0



and it mounts just fine via a Xubuntu feisty live cd.
is there a quick and easy fix to get it going on Dapper?

---

