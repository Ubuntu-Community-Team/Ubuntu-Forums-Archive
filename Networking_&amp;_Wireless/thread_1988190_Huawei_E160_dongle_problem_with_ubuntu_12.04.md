---
title: "Huawei E160 dongle problem with ubuntu 12.04"
date: 2012-05-27
forum: Networking &amp; Wireless
---

### Post by heian on 2012-05-27
Hi,

I got a Huawei E160 dongle from my provider which allowes me to use a certain amount of data per month. 

Now i'm abroad and let a shop unlock my dongle, because i want to use a local simcard.

Strange thing is that when i insert my dongle with my own sim, ubuntu asks me for the unlock code and the green led is flashing.
(didn't go any further)

When i insert the dongle with the local simcard, there is no response from ubuntu at all and the blue light is flashing.

I noticed that my E160 is now recognized as a E220 modem, but that happened to other people as well, i read somewere.

Anybody who can point me out what to do?


Here some output from what i think is important:


[COLOR="Blue"]Original simcard that comes with the dongle:[/COLOR]

heian@IdeaPad:~$ lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 002: ID 5986:0242 Acer, Inc 
Bus 008 Device 002: ID 0a5c:2150 Broadcom Corp. BCM2046 Bluetooth Device 
Bus 001 Device 009: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270/E870 HSDPA/HSUPA Modem heian@IdeaPad:~$ lsusb -v -s 09 

Bus 001 Device 009: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270/E870 HSDPA/HSUPA Modem 
Couldn't open device, some information will be missing 
Device Descriptor: 
  bLength                18 
  bDescriptorType         1 
  bcdUSB               2.00 
  bDeviceClass            0 (Defined at Interface level) 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64 
  idVendor           0x12d1 Huawei Technologies Co., Ltd. 
  idProduct          0x1003 E220 HSDPA Modem / E230/E270/E870 HSDPA/HSUPA Modem 
  bcdDevice            0.00 
  iManufacturer           2 
  iProduct                1 
  iSerial                 0 
  bNumConfigurations      1 
  Configuration Descriptor: 
    bLength                 9 
    bDescriptorType         2 
    wTotalLength          108 
    bNumInterfaces          4 
    bConfigurationValue     1 
    iConfiguration          0 
    bmAttributes         0xe0 
      Self Powered 
      Remote Wakeup 
    MaxPower              500mA 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        0 
      bAlternateSetting       0 
      bNumEndpoints           3 
      bInterfaceClass       255 Vendor Specific Class 
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x81  EP 1 IN 
        bmAttributes            3 
          Transfer Type            Interrupt 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0040  1x 64 bytes 
        bInterval               5 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x82  EP 2 IN 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval              32 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x01  EP 1 OUT 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval              32 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        1 
      bAlternateSetting       0 
      bNumEndpoints           2 
      bInterfaceClass       255 Vendor Specific Class 
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x83  EP 3 IN 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval              32 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x02  EP 2 OUT 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval              32 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        2 
      bAlternateSetting       0 
      bNumEndpoints           2 
      bInterfaceClass         8 Mass Storage 
      bInterfaceSubClass      6 SCSI 
      bInterfaceProtocol     80 Bulk-Only 
      iInterface              0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x84  EP 4 IN 
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
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        3 
      bAlternateSetting       0 
      bNumEndpoints           2 
      bInterfaceClass         8 Mass Storage 
      bInterfaceSubClass      6 SCSI 
      bInterfaceProtocol     80 Bulk-Only 
      iInterface              0 
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
        bEndpointAddress     0x85  EP 5 IN 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval


[COLOR="Blue"]Local simcard that i bought:
[/COLOR]

[COLOR="Black"]Thai Simcard

heian@IdeaPad:~$ lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 002: ID 5986:0242 Acer, Inc 
Bus 008 Device 002: ID 0a5c:2150 Broadcom Corp. BCM2046 Bluetooth Device 
Bus 001 Device 007: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270/E870 HSDPA/HSUPA Modem heian@IdeaPad:~$ lsusb -v -s 07 
 
Bus 001 Device 007: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270/E870 HSDPA/HSUPA Modem 
Couldn't open device, some information will be missing 
Device Descriptor: 
  bLength                18 
  bDescriptorType         1 
  bcdUSB               2.00 
  bDeviceClass            0 (Defined at Interface level) 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64 
  idVendor           0x12d1 Huawei Technologies Co., Ltd. 
  idProduct          0x1003 E220 HSDPA Modem / E230/E270/E870 HSDPA/HSUPA Modem 
  bcdDevice            0.00 
  iManufacturer           2 
  iProduct                1 
  iSerial                 0 
  bNumConfigurations      1 
  Configuration Descriptor: 
    bLength                 9 
    bDescriptorType         2 
    wTotalLength          108 
    bNumInterfaces          4 
    bConfigurationValue     1 
    iConfiguration          0 
    bmAttributes         0xe0 
      Self Powered 
      Remote Wakeup 
    MaxPower              500mA 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        0 
      bAlternateSetting       0 
      bNumEndpoints           3 
      bInterfaceClass       255 Vendor Specific Class 
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x81  EP 1 IN 
        bmAttributes            3 
          Transfer Type            Interrupt 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0040  1x 64 bytes 
        bInterval               5 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x82  EP 2 IN 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval              32 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x01  EP 1 OUT 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval              32 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        1 
      bAlternateSetting       0 
      bNumEndpoints           2 
      bInterfaceClass       255 Vendor Specific Class 
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x83  EP 3 IN 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval              32 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x02  EP 2 OUT 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval              32 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        2 
      bAlternateSetting       0 
      bNumEndpoints           2 
      bInterfaceClass         8 Mass Storage 
      bInterfaceSubClass      6 SCSI 
      bInterfaceProtocol     80 Bulk-Only 
      iInterface              0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x84  EP 4 IN 
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
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        3 
      bAlternateSetting       0 
      bNumEndpoints           2 
      bInterfaceClass         8 Mass Storage 
      bInterfaceSubClass      6 SCSI 
      bInterfaceProtocol     80 Bulk-Only 
      iInterface              0 
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
        bEndpointAddress     0x85  EP 5 IN 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval               0 
heian@IdeaPad:~$ 
[/COLOR]

---

