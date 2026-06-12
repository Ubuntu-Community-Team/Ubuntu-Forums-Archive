---
title: "USB modem Huawei E180v with 8.04"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by nutnut on 2010-09-09
Apparently it works with >Ubuntu 9.04, but I need 8.04..

I'd had an older modem working on the same system, so its really something to do with this newer ones. 

Symptoms:
--------
lsusb shows little, no /dev/ttyUSB\* devices

lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 12d1:140c Huawei Technologies Co., Ltd.
Bus 001 Device 001: ID 0000:0000


Kernel log:
Sep  8 15:47:55 kernel: [622229.561065] usb 1-6: USB disconnect, address 4
Sep  8 15:48:05 kernel: [622238.853020] usb 1-6: new high speed USB device using ehci_hcd and address 5
Sep  8 15:48:05 kernel: [622239.013960] usb 1-6: configuration #1 chosen from 1 choice
Sep  8 15:48:05 kernel: [622239.055187] Initializing USB Mass Storage driver...
Sep  8 15:48:05 kernel: [622239.056721] scsi10 : SCSI emulation for USB Mass Storage devices
Sep  8 15:48:05 kernel: [622239.057194] usbcore: registered new interface driver usb-storage
Sep  8 15:48:05 kernel: [622239.057202] USB Mass Storage support registered.
Sep  8 15:48:05 kernel: [622239.057563] usb-storage: device found at 5
Sep  8 15:48:05 kernel: [622239.057569] usb-storage: waiting for device to settle before scanning
Sep  8 15:48:10 kernel: [622244.044203] usb-storage: device scan complete
Sep  8 15:48:10 kernel: [622244.046187] scsi 10:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Sep  8 15:48:10 kernel: [622244.077109] sr1: scsi-1 drive
Sep  8 15:48:10 kernel: [622244.077196] sr 10:0:0:0: Attached scsi CD-ROM sr1
Sep  8 15:48:10 kernel: [622244.077264] sr 10:0:0:0: Attached scsi generic sg3 type 5

So far I've read:
----------------
[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

[http://swisscom-forum.mxm.ch/de//forum_posts.asp?TID=3976](http://swisscom-forum.mxm.ch/de//forum_posts.asp?TID=3976)

[http://www.kworx.de/2009/11/huawei-e161-usb-surfstick-unter-linux/](http://www.kworx.de/2009/11/huawei-e161-usb-surfstick-unter-linux/)

[https://wiki.ubuntu.com/NetworkManager/Hardware/3G/Probing](https://wiki.ubuntu.com/NetworkManager/Hardware/3G/Probing)

[http://www.draisberghof.de/usb_modeswitch](http://www.draisberghof.de/usb_modeswitch)
usb_modeswitch looked promising..
 
[INDENT]/usr/sbin/usb_modeswitch -c 12d1:140c
Warning: TargetProductList overrides TargetProduct!
Looking for target devices ...
 Found devices in target mode or class (1)
Looking for default devices ...
 No devices in default mode or class found. Nothing to do. Bye.
[/INDENT]

Another suggestion from [http://ubuntuforums.org/showthread.php?p=1776667](http://ubuntuforums.org/showthread.php?p=1776667)
[INDENT]lsmod|grep usb_storage
  rmmod usb-storage
  rmmod usb-serial
  lsusb
  modprobe usbserial vendor=0x12d1 product=0x140c
# now unplug the modem and back
  ls -la /dev/ttyU*
  lsusb
  lsmod|grep usb
[/INDENT]

But no luck so far, any suggestions please?

---

### Post by nutnut on 2010-09-13
fix: see:
[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=3307#3307](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=3307#3307)

---

