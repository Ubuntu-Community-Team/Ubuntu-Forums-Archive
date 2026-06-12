---
title: "Angel usb tv tuner as capture?"
date: 2011-03-03
forum: Multimedia Software
---

### Post by rayj on 2011-03-03
Hello, everyone!

I found a few threads concerning the Dell Angel USB TV tuner, but no responses. Truth is, I'm not sure where to start, and would appreciate any newbie suggestions. All I want to do is some simple composite capture of several VHS tapes.

The system sees the device:
(per lsusb as root)
> 
Bus 001 Device 005: ID 1009:0013 Emuzed, Inc. Angel MPEG Device
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1009 Emuzed, Inc.
  idProduct          0x0013 Angel MPEG Device
  bcdDevice            4.01
  iManufacturer           1 Emuzed
  iProduct                2 Angel USB
  iSerial                 3 63055052
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              16
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

I figured I'd be able to grab it with VLC, but cannot figure out how. Anything would be fine...a simple CLI utility, etc. Just want to capture classic NTSC, would love deinterlacing but not required, etc.

Any suggestions?

---

