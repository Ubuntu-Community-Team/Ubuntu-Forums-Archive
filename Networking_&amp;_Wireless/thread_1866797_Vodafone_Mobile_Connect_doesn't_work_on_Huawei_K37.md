---
title: "Vodafone Mobile Connect doesn't work on Huawei K3765"
date: 2011-10-21
forum: Networking &amp; Wireless
---

### Post by karuna.murti on 2011-10-21
lsusb:

```
Bus 002 Device 007: ID 12d1:1465 Huawei Technologies Co., Ltd. 
Bus 002 Device 003: ID 04f2:b1aa Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 004: ID 03f0:231d Hewlett-Packard 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Installed package:

```
ozerocdoff 0.4-2
vodafone-mobile-connect 2.25.01-1
```

dmesg:

```
[ 1760.515356] USB Serial support registered for generic
[ 1760.515734] usbcore: registered new interface driver usbserial_generic
[ 1760.515738] usbserial: USB Serial Driver core
[ 1760.521862] USB Serial support registered for GSM modem (1-port)
[ 1760.521971] option 2-1.2:1.0: GSM modem (1-port) converter detected
[ 1760.522404] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB0
[ 1760.522439] option 2-1.2:1.3: GSM modem (1-port) converter detected
[ 1760.522516] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB1
[ 1760.522533] option 2-1.2:1.4: GSM modem (1-port) converter detected
[ 1760.522607] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB2
[ 1760.522644] usbcore: registered new interface driver option
[ 1760.522646] option: v0.7.2:USB Driver for GSM modems
[ 1761.455887] scsi 9:0:0:0: CD-ROM            Vodafone CD ROM (Huawei)  2.31 PQ: 0 ANSI: 2
[ 1761.455938] scsi 10:0:0:0: Direct-Access     Vodafone Storage (Huawei) 2.31 PQ: 0 ANSI: 2
[ 1761.464011] sr1: scsi-1 drive
[ 1761.464201] sr 9:0:0:0: Attached scsi CD-ROM sr1
[ 1761.465796] sr 9:0:0:0: Attached scsi generic sg2 type 5
[ 1761.467250] sd 10:0:0:0: Attached scsi generic sg3 type 0
[ 1761.469365] sd 10:0:0:0: [sdb] Attached SCSI removable disk
```

vodafone-mobile-connect-card-driver-for-linux error message:

```
get_plugin_by_vendor_product_id called with 0x12D1 and 0x1465
Traceback (most recent call last):
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/_unixhardwarereg.py", line 122, in __init__
    d = self.get_devices()
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/_unixhardwarereg.py", line 151, in get_devices
    d = self._get_devices_from_udis(parent_udis)
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/_unixhardwarereg.py", line 184, in _get_devices_from_udis
    unknown_devs = map(self._get_device_from_udi, udis)
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/_unixhardwarereg.py", line 177, in _get_device_from_udi
    device = self._get_device_from_info_and_ports(info, udi, ports)
--- <exception caught here> ---
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/_unixhardwarereg.py", line 386, in _get_device_from_info_and_ports
    cport = ports[cport_index]
exceptions.IndexError: list index out of range
data port is /dev/ttyUSB0
Efective user id: 1000
```

It was working a couple days ago, but right now it is not working. I suspect because of package update, the ozerocdoff doesn't work anymore.
I've tried to manually turn off:

```
sudo ozerocdoff -i 0x1465
ERROR: No Zero-CD device found
```

Can anyone help me?

---

### Post by karuna.murti on 2011-10-22
Never mind, it was the stupidest mistake ever. I put the sim card upside down :(

---

