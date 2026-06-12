---
title: "how to keep devices active during suspended power state?"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by heldchen on 2010-09-25
i have an usb bluetooth dongle with a paired remote control. in lucid, i was able to wakeup/resume the pc from a suspended power state through the remote control, as the bluetooth dongle never was completely powered down (its led kept blinking).
 
in maverick, this seems to have changed: in suspended state, the bluetooth dongle is completely powered down (not blinking anymore). 
 
how can i exclude devices (and in particular this bluetooth dongle) from suspending in maverick? i am using bluez:
 
```
[ /org/bluez/825/hci0 ]
    Name = x-wing-0
    Powered = 1
    Devices = dev_00_23_06_ED_1C_8B
    DiscoverableTimeout = 0
    PairableTimeout = 0
    Discoverable = 0
    Address = 00:02:72:A9:3F:7C
    Discovering = 0
    Pairable = 1
    Class = 4718848
    UUIDs = 0x1112 0x111f 0x110a 0x110c 0x110e
    [ /org/bluez/825/hci0/dev_00_23_06_ED_1C_8B ]
        Name = BD Remote Control
        Paired = 0
        Adapter = /org/bluez/825/hci0
        Alias = BD Remote Control
        Connected = 0
        UUIDs = 0x1124 0x1200
        Address = 00:23:06:ED:1C:8B
        Class = 0x00250c
        Trusted = 1
        Blocked = 0
```
 
the usb dongle is a BCM2046 based dongle:
```
thomas@x-wing:~$ lsusb
...
Bus 004 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
...
```
 
and attached to the front usb port (EUSB) which is wakeup-enabled: 
```
thomas@x-wing:~$ sudo cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node
P0P1      S4    *disabled  pci:0000:00:1e.0
AZAL      S3    *disabled  pci:0000:00:1b.0
P0P4      S4    *disabled  pci:0000:00:1c.0
P0P5      S4    *disabled  pci:0000:00:1c.1
JLAN      S3    *disabled  pci:0000:02:00.5
P0P6      S4    *disabled
P0P7      S4    *disabled  pci:0000:00:1c.3
P0P8      S4    *disabled
P0P9      S4    *disabled
USB0      S3    *disabled  pci:0000:00:1d.0
USB1      S3    *disabled  pci:0000:00:1d.1
USB2      S3    *enabled   pci:0000:00:1d.2
USB3      S3    *disabled  pci:0000:00:1d.3
EUSB      S3    *enabled   pci:0000:00:1d.7

```
 
thanks for any help & pointers...

---

