---
title: "Huawei EC168C USB Stick"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by kWahab on 2010-06-08
I'm using Ubuntu Lucid 64-bit. When I attach my Huawei EC168C usb I get the following 

```

dmesg

usb 3-1: new full speed USB device using uhci_hcd and address 8
usb 3-1: configuration #1 chosen from 1 choice
scsi41 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 8
usb-storage: waiting for device to settle before scanning
usb 3-1: USB disconnect, address 8
usb 3-1: new full speed USB device using uhci_hcd and address 9
usb 3-1: configuration #1 chosen from 1 choice
option 3-1:1.0: GSM modem (1-port) converter detected
usb 3-1: GSM modem (1-port) converter now attached to ttyUSB0
option 3-1:1.1: GSM modem (1-port) converter detected
usb 3-1: GSM modem (1-port) converter now attached to ttyUSB1
option 3-1:1.2: GSM modem (1-port) converter detected
usb 3-1: GSM modem (1-port) converter now attached to ttyUSB2
scsi45 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 9
usb-storage: waiting for device to settle before scanning
option 3-1:1.4: GSM modem (1-port) converter detected
usb 3-1: GSM modem (1-port) converter now attached to ttyUSB3

```

ttyUSB2 is the correct modem that gets me connected to the Internet by using wvdial.

After attaching the device I get a **New Mobile Broadband (CDMA) Connection...**
The wizard never asks which device to use and assumes it is ttyUSB0 which doesn't work.

**How can I change it to use ttyUSB2 instead of ttyUSB0?**

Here is the output from /var/log/daemon.log
```


modem-manager: (Huawei): CDMA modem /sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1 claimed port ttyUSB0
modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1
modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1 as /org/freedesktop/ModemManager/Modems/3
NetworkManager: <info>  (ttyUSB0): new CDMA device (driver: 'option1')
NetworkManager: <info>  (ttyUSB0): exported as /org/freedesktop/NetworkManager/Devices/7
NetworkManager: <info>  (ttyUSB0): now managed
NetworkManager: <info>  (ttyUSB0): device state change: 1 -> 2 (reason 2)
NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 2).
NetworkManager: <info>  (ttyUSB0): device state change: 2 -> 3 (reason 0)
modem-manager: (ttyUSB1): re-checking support...
modem-manager: (ttyUSB2): re-checking support...
modem-manager: (ttyUSB1) opening serial device...
modem-manager: (ttyUSB1): probe requested by plugin 'Huawei'
modem-manager: (ttyUSB2) opening serial device...
modem-manager: (ttyUSB2): probe requested by plugin 'Huawei'
modem-manager: (ttyUSB3): re-checking support...
modem-manager: (ttyUSB3) opening serial device...
modem-manager: (ttyUSB3): probe requested by plugin 'Huawei'
modem-manager: (ttyUSB2) closing serial device...
modem-manager: (Huawei): CDMA modem /sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1 claimed port ttyUSB2
modem-manager: (ttyUSB1) closing serial device...
modem-manager: (ttyUSB3) closing serial device...
NetworkManager: <info>  Activation (ttyUSB0) starting connection 'WorldCall connection'
NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 (reason 0)
NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
modem-manager: (ttyUSB0) opening serial device...
modem-manager: Modem /org/freedesktop/ModemManager/Modems/3: state changed (disabled -> enabling)
modem-manager: (ttyUSB2) opening serial device...
modem-manager: Modem /org/freedesktop/ModemManager/Modems/3: state changed (enabling -> enabled)
NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 3 (reason 39)
NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 39).


```

---

