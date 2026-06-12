---
title: "configuring cdma evdo modem"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by makan on 2010-12-20
hi,

i have a cdma evdo modem that i cannot configure it properly on my ubuntu 10.04. it has a label "Exiss Mobile".

my problem is "i cannot switch my device mode from mass storage to modem"
from: Bus 002 Device 005: ID 8888:6500
to: Bus 002 Device 010: ID 16d8:6533 CMOTECH Co., Ltd.

i have set my usb-modeswitch.conf, and give me the message below when i'm running "sudo usb_modeswitch -W" but it did not change/switch :

```

Reading config file: /etc/usb-modeswitch.conf

 * usb-modeswitch: handle USB devices with multiple modes
 * Version 1.1.0 (C) Josua Dietze 2010
 * Based on libusb 0.1.12

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x8888
DefaultProduct= 0x6500
TargetVendor=   0x16d8
TargetProduct=  0x6533
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
GCTMode=0
MessageEndpoint= not set
MessageContent="5553424312345678c00000008000069f030000000000000000000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled
System integration mode disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 005 on 002
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 001 on 001

Looking for target devices ...
  searching devices, found USB ID 8888:6500
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0002
 No devices in target mode or class found
Looking for default devices ...
  searching devices, found USB ID 8888:6500
   found matching vendor ID
   found matching product ID
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0002
 Found default devices (1)
Accessing device 005 on bus 002 ...
Using endpoints 0x05 (out) and 0x85 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String:         
   Model String: Mass Storage    
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: PART 3 SYSTEM CO.,LTD
     Product: PART 3 CDMA Technologies
  Serial No.: Serial Number
-------------------------
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x05 ...
 OK, message successfully sent
-> Run lsusb to note any changes. Bye.

```

for now, the only way for utilize this modem is by running ms windows on my virtuabox and enable it on virtualbox's usb devices. when it set, i can turn off my virtual machine and use the modem on ubuntu.

---

### Post by alexfish on 2010-12-20
Hi

usb_modeswitch have a dedicated forum

suggest visiting 

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

submit details of how the device is seen from the command "lsusb"

or possibly from

Code:

usb-devices

whilst the device may be getting detected , the important bit is the 
message content and possible other info , from what i see the message content
does not look like the family of C-motech

alexfish

Added : Sometimes VM ware can  switch the device but can make life difficult for the usb_modeswitch (on the linux side) suggest mentioning this at the forum

---

### Post by makan on 2010-12-21
thank you alexfish for your respond.

i will consult this issue to usb_modeswitch forum

thank you.
;)

---

### Post by possumkeys on 2010-12-30
When i input usb_modeswitch, i got no  vendor or product id specified. Does this mean that for the default and target vendor id for my modem, i should input them in usb_modeswitch.conf file?

---

### Post by makan on 2011-01-06
after small discussion at usb_modeswitch forum, now i can operate my modem properly.

this is my usb_modeswitch config

```

DefaultVendor=  0x8888 
DefaultProduct= 0x6500
 
TargetVendor=   0x16d8
TargetProduct=  0x6533

MessageContent="5553424398e2c4812400000080000bff524445564348473d43440000000000"

NeedResponse=1

```

now i don't have to run my virtualbox to switch it anymore.

thank you alexfish
):P

---

