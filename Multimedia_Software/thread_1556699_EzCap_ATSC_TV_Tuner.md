---
title: "EzCap ATSC TV Tuner"
date: 2010-08-19
forum: Multimedia Software
---

### Post by RemmyLee on 2010-08-19
I recieved a USB ATSC TV Tuner today and was wondering if anyone could help me get it going. The info I've gathered:

lsusb output:
```
eb1a:2875 eMPIA Technology, Inc.
```

lsusb -v output:
```
Bus 002 Device 004: ID eb1a:2875 eMPIA Technology, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0xeb1a eMPIA Technology, Inc.
  idProduct          0x2875 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 USB 2875 Device
  iSerial                 2 10101010
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03ac  1x 940 bytes
        bInterval               1
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

Perusing the internet brought to this being an em28xx driver tuner. However, after loading it, nothing seems to change. Any advice would be appreciated.

---

### Post by wesleybishop on 2010-11-07
Bump

---

### Post by ^^Johnny5 on 2011-05-25
Have you been able to get this device going?
I have the exact same device, can't seem to get w_scan to work on it.
Ubuntu 11.04 64

---

### Post by n3gbz on 2012-05-21
I just encountered same problem with a TV tuner received today.  Did you ever get it resolved?

---

### Post by fixitdude on 2012-05-21
What does dmesg say when you plug it in?

You have to at least see if it loads some drivers.

---

### Post by jmore9 on 2012-05-21
If you go to :

[http://linuxtv.org/wiki/index.php/Main_Page](http://linuxtv.org/wiki/index.php/Main_Page)

This site has almost everything about getting supported devices running under linux.  It has a list of known devices that work and some that do not work.

Hope this helps.

---

### Post by n3gbz on 2012-05-25
> **fixitdude said:**
> What does dmesg say when you plug it in?

You have to at least see if it loads some drivers.

dmesg:

[21966.456090] usb 1-3: new high-speed USB device number 5 using ehci_hcd

lsusb:

Bus 001 Device 005: ID 0db0:8810 Micro Star International 

hwinfo --usb:

15: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: 2UT6.3ceaCRc1_t6
  Parent ID: k4bc.OqydEZZ981A
  SysFS ID: /devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3:1.0
  SysFS BusID: 1-3:1.0
  Hardware Class: unknown
  Model: "Micro Star International USB 2875 Device"
  Hotplug: USB
  Vendor: usb 0x0db0 "Micro Star International"
  Device: usb 0x8810 "USB 2875 Device"
  Revision: "1.00"
  Serial ID: "0"
  Speed: 480 Mbps
  Module Alias: "usb:v0DB0p8810d0100dc00dsc00dp00icFFisc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #8 (Hub)


------------------------------

I can not find it listed anywhere as a supported device.

---

