---
title: "Tata photon EC1260 not working on Ubuntu 12.04"
date: 2013-01-25
forum: Networking &amp; Wireless
---

### Post by poojasaxena on 2013-01-25
Dear all, 
Earlier I was working on 10.04 and google helped me in working of tata photon plus, model EC1260. 
Recently, I installed 12.04 LTS version on my DELL laptop. And not it is not working anymore. I did google and tried couples of things, but all in vain. 

Already followed the most common solution provided online: [http://smashingweb.info/tata-photon-plus-huawei-ec156-modem-in-ubuntu-fedora/](http://smashingweb.info/tata-photon-plus-huawei-ec156-modem-in-ubuntu-fedora/)


I am afraid it is the only source of internet at home. Please help with this.

Thanks in advance,
pooja

---

### Post by poojasaxena on 2013-01-25
Please find the output [2] of the following command:
sudo usb_modeswitch -I -W -c 12d1\:1505

And the content of the 12d1\:1505 is [1]

Please let me know if any more information is needed. 

[1]
=========================================
DefaultVendor= 0x12d1
DefaultProduct=0x1505

TargetVendor=  0x12d1
TargetProduct= 0x140b

MessageContent="55534243123456780000000000000011062000000100000000000000000000"

CheckSuccess=20


[2]
=========================================
sudo usb_modeswitch -I -W -c 12d1\:1505 
[sudo] password for pooja: 

Reading config file: 12d1:1505

 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.2.3 (C) Josua Dietze 2012
 * Based on libusb0 (0.1.12 and above)

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x12d1
DefaultProduct= 0x1505
TargetVendor=   0x12d1
TargetProduct=  0x140b
TargetClass=    not set
TargetProductList=""

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
QisdaMode=0
GCTMode=0
KobilMode=0
SequansMode=0
MobileActionMode=0
CiscoMode=0
MessageEndpoint=  not set
MessageContent="55534243123456780000000000000011062000000100000000000000000000"
NeedResponse=0
ResponseEndpoint= not set

InquireDevice disabled
Success check enabled, max. wait time 20 seconds
System integration mode disabled


usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 012 on 002
usb_os_find_devices: Found 008 on 002
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 002 on 002
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 008 on 001
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 007 on 001
skipped 1 class/vendor specific interface descriptors
skipping descriptor 0xFF
skipped 1 class/vendor specific endpoint descriptors
usb_os_find_devices: Found 006 on 001
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 004 on 001
skipping descriptor 0xFF
skipping descriptor 0xB
skipped 2 class/vendor specific endpoint descriptors
skipped 6 class/vendor specific interface descriptors
skipping descriptor 0x25
skipped 1 class/vendor specific endpoint descriptors
skipped 11 class/vendor specific interface descriptors
usb_os_find_devices: Found 003 on 001
usb_os_find_devices: Found 002 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
Looking for target devices ...
  searching devices, found USB ID 12d1:140b
   found matching vendor ID
   found matching product ID
   adding device
  searching devices, found USB ID 046d:c063
  searching devices, found USB ID 8087:0020
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 413c:8160
  searching devices, found USB ID 413c:8162
  searching devices, found USB ID 413c:8161
  searching devices, found USB ID 0c45:641d
  searching devices, found USB ID 0a5c:4500
  searching devices, found USB ID 8087:0020
  searching devices, found USB ID 1d6b:0002
 Found devices in target mode or class (1)
Looking for default devices ...
  searching devices, found USB ID 12d1:140b
   found matching vendor ID
  searching devices, found USB ID 046d:c063
  searching devices, found USB ID 8087:0020
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 413c:8160
  searching devices, found USB ID 413c:8162
  searching devices, found USB ID 413c:8161
  searching devices, found USB ID 0c45:641d
  searching devices, found USB ID 0a5c:4500
  searching devices, found USB ID 8087:0020
  searching devices, found USB ID 1d6b:0002
 No devices in default mode found. Nothing to do. Bye.

---

