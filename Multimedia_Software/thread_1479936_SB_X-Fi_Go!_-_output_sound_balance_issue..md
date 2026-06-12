---
title: "SB X-Fi Go! - output sound balance issue."
date: 2010-05-11
forum: Multimedia Software
---

### Post by andyshuz on 2010-05-11
Hello,  
I use USB soundcard SB X-Fi Go! and output level for right channel is much higher than left one. I've checked all possible places for balance configuration (as I think) and everywhere it is set to equal. Does somebody knows where the problem could be and how to fix it? 

Just in case, there is dmesg for this device:
> [430638.068026] usb 2-9: new full speed USB device using ohci_hcd and address 32
[430638.295215] usb 2-9: configuration #1 chosen from 1 choice
[430638.673738] scsi22 : SCSI emulation for USB Mass Storage devices
[430638.682586] usb-storage: device found at 32
[430638.682593] usb-storage: waiting for device to settle before scanning
[430643.683485] usb-storage: device scan complete
[430643.690089] scsi 22:0:0:0: Direct-Access              SB X-Fi Go!           PQ: 0 ANSI: 3
[430643.690921] sd 22:0:0:0: Attached scsi generic sg2 type 0
[430643.712056] sd 22:0:0:0: [sdb] 1970176 512-byte logical blocks: (1.00 GB/962 MiB)
[430643.719041] sd 22:0:0:0: [sdb] Write Protect is on
[430643.719049] sd 22:0:0:0: [sdb] Mode Sense: 0b 00 80 00
[430643.719055] sd 22:0:0:0: [sdb] Assuming drive cache: write through
[430643.745049] sd 22:0:0:0: [sdb] Assuming drive cache: write through
[430643.745062]  sdb:
[430643.784050] sd 22:0:0:0: [sdb] Assuming drive cache: write through
[430643.784062] sd 22:0:0:0: [sdb] Attached SCSI removable disk
[430653.519097] usb 2-9: USB disconnect, address 32
[430653.523076] cannot submit datapipe for urb 0, error -19: no device
[430654.676841] usb 2-9: new full speed USB device using ohci_hcd and address 33
[430655.253025] usb 2-9: device not accepting address 33, error -62
[430655.308048] hub 2-0:1.0: unable to enumerate USB device on port 9
[430656.428039] usb 2-9: new full speed USB device using ohci_hcd and address 35
[430656.655217] usb 2-9: configuration #1 chosen from 1 choice
[430657.029495] scsi23 : SCSI emulation for USB Mass Storage devices
[430657.037545] usb-storage: device found at 35
[430657.037552] usb-storage: waiting for device to settle before scanning
[430662.039099] usb-storage: device scan complete
[430662.046077] scsi 23:0:0:0: Direct-Access              SB X-Fi Go!           PQ: 0 ANSI: 3
[430662.046801] sd 23:0:0:0: Attached scsi generic sg2 type 0
[430662.097071] sd 23:0:0:0: [sdb] 1970176 512-byte logical blocks: (1.00 GB/962 MiB)
[430662.104055] sd 23:0:0:0: [sdb] Write Protect is on
[430662.104067] sd 23:0:0:0: [sdb] Mode Sense: 0b 00 80 00
[430662.104072] sd 23:0:0:0: [sdb] Assuming drive cache: write through
[430662.132096] sd 23:0:0:0: [sdb] Assuming drive cache: write through
[430662.132110]  sdb:
[430662.175051] sd 23:0:0:0: [sdb] Assuming drive cache: write through
[430662.175064] sd 23:0:0:0: [sdb] Attached SCSI removable disk

---

