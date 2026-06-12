---
title: "libgphoto2 support for Disney Pix Micro"
date: 2008-12-26
forum: Multimedia Software
---

### Post by pjman on 2008-12-26
I'm trying to get pictures off of a cheap Disney Pix Micro camera. People [_have stated_]("http://ubuntuforums.org/showthread.php?t=501176") that it works with older versions of Ubuntu but I cannot view pictures on the camera with Hardy.

The latest version of libgphoto2 (2.4.3) has [_experimental support_]("http://www.gphoto.org/proj/libgphoto2/support.php"). Hardy comes with 2.4.0. I cannot find the camera support list for 2.4.0.

A few questions:

Why would the camera work with 7.10 and not 8.04?
How would I go about upgrading libgphoto2 from 2.4.0 to 2.4.3 to see if this helps?

Thanks for your help!


**update**

I also found this link - [http://www.qbik.ch/usb/devices/showdev.php?id=4131](http://www.qbik.ch/usb/devices/showdev.php?id=4131)

It sounds like it should work. I'm not sure what I'm doing wrong. When I connect the camera lsusb -v is showing this info on the device:

> Bus 001 Device 018: ID 2770:9052 NHJ, Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0         8
  idVendor           0x2770 NHJ, Ltd
  idProduct          0x9052 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                2 USB Digital Still Camera
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
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
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval               3
Device Status:     0x0000
  (Bus Powered)

gnome-device-manager is saying "Insufficient power to operate USB device." even though I know it's a USB 2.0 connection to my PC.

Any other ideas?

---

### Post by Databit on 2008-12-31
did you have any luck with this? I'm trying to get the same thing and coming up empty handed

---

### Post by xc3RnbFO8P on 2009-01-01
Read this:
[http://ubuntuforums.org/showthread.php?t=1022088]("http://ubuntuforums.org/showthread.php?t=1022088")

---

### Post by cjbarnes18 on 2010-12-30
I have found that Gtkam works reasonably well in 10.10.

---

