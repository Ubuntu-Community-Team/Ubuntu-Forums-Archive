---
title: "Ralink wireless USB device detected but won't load driver"
date: 2006-02-28
forum: Networking &amp; Wireless
---

### Post by clee991 on 2006-02-28
I have tried both the CVS and beta rt2570 drivers and Ralink rt73 driver followed the readme's and searched here and serialmonkey forum but without being able to even get started. Any suggestions on how to troubleshoot my way through this would be much appreciated. My system info follows

Thx

chris

Tested USB wireless device OK under WinXP sp2 with rt2500usb.sys driver

Ubuntu 5.10 Breezy 2.6.12-10-386

dmesg

[4307519.078000] SCSI subsystem initialized
[4308767.330000] usbcore: registered new driver rtusb
[4310744.617000] usbcore: deregistering driver rtusb
[4310744.619000] <===usb_rtusb_exit
[4310856.158000] usbcore: registered new driver rtusb
[4316007.916000] usbcore: deregistering driver rtusb
[4316007.978000] <===usb_rtusb_exit
[4317154.384000] usbcore: registered new driver rtusb

lsmod

Module Size Used by
rt2570 208320 0
sg 33696 0

lshw

*-usb:2
description: USB Controller
product: USB 2.0 Controller
vendor: Silicon Integrated Systems [SiS]
physical id: 3.3
bus info: pci@00:03.3
version: 00
width: 32 bits
clock: 33MHz
capabilities: ehci bus_master cap_list
configuration: driver=ehci_hcd
resources: iomemory:f1800000-f1800fff irq:23
*-usbhost
product: Silicon Integrated Systems [SiS] USB 2.0 Controller
vendor: Linux 2.6.12-10-386 ehci_hcd
physical id: 1
bus info: usb@3
logical name: usb3
version: 2.06
capabilities: usb-2.00
configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
*-usb UNCLAIMED
description: Generic USB device
product: 802.11g WLAN + Pen Drive
vendor: Ralink
physical id: 1
bus info: usb@3:1
version: 0.01
capabilities: usb-2.00
configuration: maxpower=300mA speed=480.0MB/s

---

### Post by Teroedni on 2006-02-28
write```
sudo gedit /etc/network/interfaces

```

you get a text file


post it here
[COLOR="Red"]Warning!!![/COLOR]:If you got encryption set up! make sure to remove that info before hitting submit, so we dont see your password  or key [COLOR="Red"]Warning!!![/COLOR]

---

### Post by clee991 on 2006-02-28
interfaces attached

---

