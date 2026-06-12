---
title: "Cable modem on USB, limited speed ?"
date: 2012-04-16
forum: Networking &amp; Wireless
---

### Post by lulaz on 2012-04-16
Hello,

At first sorry for my english, I hope you will understand me.

I have a Ubuntu 11.04 box. There is a cable modem (motorola sbg900) plugged in via USB. My bandwidth should be 8mbit download and 0,7mbit upload. Some time ago everything worked just fine, but for last couple of weeks I couldnt download faster than 400-450kB/s. Today I took a closer look at this and it seems that USB connection is the problem. I tried connecting to the modem via RJ45, and max download speed was 8mbit (good). I went back to USB and nothing more than 400-450kB/s (so 4mbits).

I have no idea whats wrong. I cant use RJ45 - I have to use USB connection to the cable modem.

Please help..

```
$ uname -a
Linux NAS 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux
``````
$ sudo lsusb -v -s 004:004

Bus 004 Device 004: ID 07b2:0900 Motorola BCS, Inc. SURFboard Gateway
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        32
  idVendor           0x07b2 Motorola BCS, Inc.
  idProduct          0x0900 SURFboard Gateway
  bcdDevice            1.01
  iManufacturer           1 Motorola Corporation
  iProduct                2 USB Cable Modem
  iSerial                 3 XXXXXXXXXXXX
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           80
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          4 USB Ethernet Configuration
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    ** UNRECOGNIZED:  05 24 00 10 01
    ** UNRECOGNIZED:  05 24 06 00 01
    ** UNRECOGNIZED:  0d 24 0f 03 00 00 00 00 ea 05 00 00 00
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      6 Ethernet Networking
      bInterfaceProtocol      0 
      iInterface              5 Communication Interface Class
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              64
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              6 Data Interface Class
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              6 Data Interface Class
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0001
  Self Powered
```

---

### Post by gordintoronto on 2012-04-16
That's the speed of USB 2.0. If you want faster, use RJ45.

---

### Post by lulaz on 2012-04-17
> **gordintoronto said:**
> That's the speed of USB 2.0. If you want faster, use RJ45.

According to Wikipedia USB 2.0 has maximum bandwidth of *480 Mbit/s* (60 MB/s). I have 450kB/s (so about 4Mbit/s).

---

### Post by lulaz on 2012-04-17
Here is output from "hwinfo" for USB port where cable modem is plugged in:
```
  usb device: name = 4-1:1.0
    path = /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.0
    modalias = "usb:v07B2p0900d0101dc02dsc00dp00ic02isc06ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 2
    bInterfaceSubClass = 6
    bInterfaceProtocol = 0
    if: 4-1:1.0 @ /devices/pci0000:00/0000:00:06.0/usb4/4-1
    bDeviceClass = 2
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x07b2
    idProduct = 0x0900
    manufacturer = "Motorola Corporation"
    product = "USB Cable Modem"
    serial = "00XXXXXXXXXXX"
    bcdDevice = 0101
    speed = "12"
```I assume that "speed = 12" means, that USB (1.1) is working in "Full Speed" (12 Mbit/s). That could be true: Motorola SBG900 supports only USB 1.1. Other USB devices connected with this computer have "speed = 480" (USB 2.0 Hi-speed). So it seems that the problem is somewhere else... Does anyone have any ideas ? ;(

---

