---
title: "AX320 ZTE WiMAX USB MODEM"
date: 2011-03-27
forum: Networking &amp; Wireless
---

### Post by george2000 on 2011-03-27
Hi, i am new to ubuntu. i am trying to get me [AX320 ZTE WiMAX USB]("http://www.wateen.com/AX320_User_Manual_20100513.pdf") Modem to work in Ubuntu. This modem when inserted in a windows system, runs its application that installs drivers if not already installed and launches connection manager. Connection manager searches for the network, connects and make a  LAN connection in windows.

When i insert this USB in my Ubuntu system, it says unformatted file system. Please suggest that is it possible? if possible give me step by step instructions. 

The service operator does not provide any support for linux.

---

### Post by adnanmoghal on 2011-05-07
Hi, Same problem here. Kindly if someone have some information about it please do reply.
Regards

---

### Post by DART5 on 2011-12-14
You'll need to use usb-modeswitch to switch out from Zero CD mode.

use this configuration:
```
########################################################
# ZTE AX320 WiMAX modem (Beceem BCSB200/BCSR200 chipset)

DefaultVendor= 0x19d2
DefaultProduct=0x0065

TargetVendor=  0x19d2
TargetProduct= 0x0044

MessageContent="55534243D0BB4D030010000080000AF2010900000000000200000000000000"

```

on success, try to find some pre-compiled drivers for that chipset. there is come project about that on google code hosting.
there is also a Staging driver in kernel.
also you can download Sprint 4G development pack and try to compile driver yourself. use [this]("http://www.opennet.ru/tips/info/2468.shtml") guide (in Russian) for that.

---

### Post by DART5 on 2011-12-14
btw, you'll also need some userspace soft:
library for modem management
encryption library
wimaxd - wimax daemon

I don't know other way to get it except compiling from source provided by Sprint 4G Developer Pack

---

