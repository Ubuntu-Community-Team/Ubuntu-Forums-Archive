---
title: "NetworkManager won't connect to my 3D adapter, but it does on Gnome"
date: 2013-03-19
forum: Networking &amp; Wireless
---

### Post by Stonecold1995 on 2013-03-19
I'm trying to use the 3G/4G Virgin Mobile USB adaptor (U600), but NetworkManager doesn't detect it automatically on Kubuntu.  I booted into Kali Linux (which uses Gnome), and instantly the NetworkManager there detected it and allowed me to configure it.  Looking online shows that there seems to be some random problems with the driver or something.

I read it's possible to connect it as a modem through KPPP, but in order to do that, I have to select the "usbTTY".  The problem is that the lack of a (functional) driver prevents this from happening.

Here's the output of the end of dmesg after plugging it in:
```
[  311.900042] usb 1-1.2.2: new full-speed USB device number 6 using ehci_hcd
[  311.994027] usb 1-1.2.2: New USB device found, idVendor=1fac, idProduct=0150
[  311.994039] usb 1-1.2.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  311.994045] usb 1-1.2.2: Product: USB Micro SD Storage
[  311.994050] usb 1-1.2.2: Manufacturer: Franklin Wireless Corp.
[  311.994055] usb 1-1.2.2: SerialNumber: 214784662300
[  312.001826] Initializing USB Mass Storage driver...
[  312.001897] scsi6 : usb-storage 1-1.2.2:1.0
[  312.001966] usbcore: registered new interface driver usb-storage
[  312.001968] USB Mass Storage support registered.
[  313.001358] scsi 6:0:0:0: CD-ROM            Franklin Auto-Installer   2.31 PQ: 0 ANSI: 0
[  313.037294] sr1: scsi3-mmc drive: 0x/0x caddy
[  313.037748] sr 6:0:0:0: Attached scsi CD-ROM sr1
[  313.038063] sr 6:0:0:0: Attached scsi generic sg3 type 5
[  313.178093] usb 1-1.2.2: reset full-speed USB device number 6 using ehci_hcd
[  313.353868] usb 1-1.2.2: reset full-speed USB device number 6 using ehci_hcd
[  313.529761] usb 1-1.2.2: reset full-speed USB device number 6 using ehci_hcd
[  313.705336] usb 1-1.2.2: reset full-speed USB device number 6 using ehci_hcd
[  313.873280] usb 1-1.2.2: reset full-speed USB device number 6 using ehci_hcd
[  314.048980] usb 1-1.2.2: reset full-speed USB device number 6 using ehci_hcd
[  314.224567] usb 1-1.2.2: reset full-speed USB device number 6 using ehci_hcd
[  314.400450] usb 1-1.2.2: reset full-speed USB device number 6 using ehci_hcd
```

The output of lsusb is:
```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 002 Device 003: ID 147e:1002 Upek
Bus 002 Device 004: ID 5986:0361 Acer, Inc
Bus 001 Device 006: ID 1fac:0150
```



In fact, the NetworkManager on Kubuntu doesn't even HAVE the "mobile broadband" tab at all (see attached screenshot).

I need to be able to get this working as soon as I can, so any kind of help or advice would be appreciated!

---

### Post by Stonecold1995 on 2013-03-21
bump

---

### Post by bmork on 2013-03-21
> **Stonecold1995 said:**
> Here's the output of the end of dmesg after plugging it in:
```
[  311.900042] usb 1-1.2.2: new full-speed USB device number 6 using ehci_hcd
[  311.994027] usb 1-1.2.2: New USB device found, idVendor=1fac, idProduct=0150
[  311.994039] usb 1-1.2.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  311.994045] usb 1-1.2.2: Product: USB Micro SD Storage
[  311.994050] usb 1-1.2.2: Manufacturer: Franklin Wireless Corp.
[  311.994055] usb 1-1.2.2: SerialNumber: 214784662300
[  312.001826] Initializing USB Mass Storage driver...
[  312.001897] scsi6 : usb-storage 1-1.2.2:1.0
[  312.001966] usbcore: registered new interface driver usb-storage
[  312.001968] USB Mass Storage support registered.
[  313.001358] scsi 6:0:0:0: CD-ROM            Franklin Auto-Installer   2.31 PQ: 0 ANSI: 0

```

This device needs to switch from "Windows driver install mode" to "modem mode" like so many other such devices.  Installing the usb-modeswitch package should fix that.

---

### Post by Stonecold1995 on 2013-03-23
> **bmork said:**
> This device needs to switch from "Windows driver install mode" to "modem mode" like so many other such devices.  Installing the usb-modeswitch package should fix that.
I have usb-modeswitch already installed, but I'm still having the problem.  And I really have no idea how to use usb-modeswitch.

---

