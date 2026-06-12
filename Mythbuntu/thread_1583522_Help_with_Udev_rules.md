---
title: "Help with Udev rules"
date: 2010-09-28
forum: Mythbuntu
---

### Post by jimp180 on 2010-09-28
I have 2 Hauppauge wintv pvr usb2 tuners and I need to write a separate rule for each. if not, on boot they show up as different video devices each time (may show up as /dev/video2 or may show up as /dev/video5..ect) and this doesn't work well for my backend tuner setup. 

when I do an udevadm attribute walk I get the exact same results (well none really) from both devices:

```
looking at device '/devices/virtual/video4linux/video2':
    KERNEL=="video2"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{name}==""
    ATTR{index}=="0"

```

```
looking at device '/devices/virtual/video4linux/video4':
    KERNEL=="video4"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{name}==""
    ATTR{index}=="0"
```

but if I run lsusb -v I can see that the computer can distinguish between them:

```
Bus 001 Device 004: ID 2040:2900 Hauppauge 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x2040 Hauppauge
  idProduct          0x2900 
  bcdDevice            4.00
  iManufacturer           1 Hauppauge
  iProduct                2 USB Device
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           60
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
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 

```

```
Bus 001 Device 003: ID 2040:2400 Hauppauge 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x2040 Hauppauge
  idProduct          0x2400 
  bcdDevice            8.00
  iManufacturer           1 Hauppauge
  iProduct                2 WinTV
  iSerial                 3 2401-00-0081BE0F
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           60
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
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 

```

How can I make udev see the product ID's that lsusb sees so I can include them in my rules? or is there something else I can do?

---

### Post by goffa on 2010-09-28
I found the guides below useful for making video and remote input devices static. The first one is probably more relevant for your requirements.

[http://www.mythtv.org/wiki/Device_Filenames_and_udev](http://www.mythtv.org/wiki/Device_Filenames_and_udev)

[http://parker1.co.uk/mythtv_tips.php](http://parker1.co.uk/mythtv_tips.php)

---

