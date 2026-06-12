---
title: "USB dongle quarrels with modules (rt2870sta)"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by zipeppe on 2010-10-06
Hey,

that's interesting for me.
Ubuntu 10.10rc fresh installation, and Wireless Adapter based on Ralink RT2870.

**lsusb **
```

Bus 001 Device 004: ID 083a:7522 Accton Technology Corp. Arcadyan 802.11N Wireless Adapter

```

**lsusb -v**
```

Bus 001 Device 004: ID 083a:7522 Accton Technology Corp. Arcadyan 802.11N Wireless Adapter
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x083a Accton Technology Corp.
  idProduct          0x7522 Arcadyan 802.11N Wireless Adapter
  bcdDevice            1.01
  iManufacturer           1 Ralink
  iProduct                2 802.11 n WLAN
  iSerial                 3 1.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           67
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              450mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           7
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 1.0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```

If the system boots with the USB adapter inserted, it loads the following modules:
```

rt2870sta
rt2800usb
rt2800lib
rt2x00usb
rt2x00lib
```

and the adapted does not work properly since it connect/disconnect continuously.

I have to remove the adapter, unload all the modules, reconnect the adapter and load ONLY the rt2870sta module with:
[INDENT]**modprobe rt2870sta**[/INDENT]

Interesting, I have added all the unwanted modules into the blacklist:

**[INDENT]tail /etc/modprobe.d/blacklist.conf[/INDENT]**

```
...
#**** the wireless
blacklist rt2x00usb rt2x00lib rt2800usb rt2800lib

```


Why the system automatically loads  unwanted modules?

:)

---

### Post by chili555 on 2010-10-06
> blacklist rt2x00usb rt2x00lib rt2800usb rt2800libThis is incorrect. It should read:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```There is no rt2800lib; viz:> $ modinfo rt2800lib
ERROR: modinfo: could not find module rt2800libPlease amend your blacklist file and reboot. Post back if it's not fixed.

---

### Post by zipeppe on 2010-10-06
> **chili555 said:**
> This is incorrect. It should read:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```There is no rt2800lib; viz:Please amend your blacklist file and reboot. Post back if it's not fixed.

Thank you chili,

you're right: it needs to be splitted in several lines!

Nevertheless the module **rt2800lib** is present on my system:
**[INDENT]modinfo rt2800lib[/INDENT]**
```
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    rt2800 library
author:         Bartlomiej Zolnierkiewicz
srcversion:     9BB37C591ED4A83F8654172
depends:        rt2x00lib,rt2x00usb
vermagic:       2.6.35-22-generic SMP mod_unload modversions 686 

```

---

### Post by chili555 on 2010-10-06
Ahh! I see, now: 10.10rc. Does it load? If so, just blacklist it and you should be all set.

---

### Post by zipeppe on 2010-10-07
> **chili555 said:**
> Ahh! I see, now: 10.10rc. Does it load? If so, just blacklist it and you should be all set.

YES, thank you. It works now as expected :P

---

