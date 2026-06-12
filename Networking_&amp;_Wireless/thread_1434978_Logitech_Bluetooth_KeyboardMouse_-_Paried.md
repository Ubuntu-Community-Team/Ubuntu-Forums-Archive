---
title: "Logitech Bluetooth Keyboard/Mouse - Paried??"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by slipdipper on 2010-03-21
Hey guys, i'm using a logitech dinovo keyboard/mouse and was trying to figure out if the device is still in boot mode. I don't see the usb hub listed when i hciconfig and i although the udev rules appear to hid2hci, i cant seem to figure out how in the heck i could be paired when i've never went through the process..

lsusb also shows "boot interface subclass" which im guessing means its in bootmode? 

Im obviously concerned about this because bootmode isnt encrypted.. any help would be much appreciated! im running karmic.. 

```

Bus 002 Device 006: ID 046d:c704 Logitech, Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc704
  bcdDevice           24.04
  iManufacturer           1 Logitech
  iProduct                2 USB Receiver
  iSerial                 3 1BEE72
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0
      ** UNRECOGNIZED:  09 21 10 01 00 01 22 3b 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0
      ** UNRECOGNIZED:  09 21 10 01 00 01 22 a8 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)


```

---

### Post by blackmail on 2010-03-21
I have had some problems with similar devices, and my harsh advice is to get something that does not die on you when you use linux, manufacturers are just too lazy to make drivers for stuff in linux, and the people coding the kernel just can't think of all the stuff! I know it sounds harsh but unless you get a linux coder/developer to help you with this you can't quite do many things...

---

### Post by slipdipper on 2010-07-11
i got it working: 
[http://ubuntuforums.org/showthread.php?p=9574808](http://ubuntuforums.org/showthread.php?p=9574808)

---

