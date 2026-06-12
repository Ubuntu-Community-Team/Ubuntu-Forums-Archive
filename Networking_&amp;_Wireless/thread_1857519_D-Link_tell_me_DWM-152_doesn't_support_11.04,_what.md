---
title: "D-Link tell me DWM-152 doesn't support 11.04, what next?!"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by daveloh on 2011-10-10
I had communicated D-Link and they said adapter above, didn't support 11.04.....i am very down...how can it be, Linux platform is so usual right now..haiz....

I search around in forum, dun seem the solution is working, and the driver giving is 32-bit, i force it to install...still not working.

I am using 64bit OS.....anyone had solve this problem?

---

### Post by daveloh on 2011-10-11
no one? anyone?
me alone~~

---

### Post by lkjoel on 2011-10-11
Try this: [http://say-linux.blogspot.com/2010/07/using-d-link-3g-usb-dwm-152-with-ubuntu.html](http://say-linux.blogspot.com/2010/07/using-d-link-3g-usb-dwm-152-with-ubuntu.html)

---

### Post by daveloh on 2011-10-11
> **lkjoel said:**
> Try this: [http://say-linux.blogspot.com/2010/07/using-d-link-3g-usb-dwm-152-with-ubuntu.html](http://say-linux.blogspot.com/2010/07/using-d-link-3g-usb-dwm-152-with-ubuntu.html)

they had sent me "DataCardDrvPkg.deb" that only support 32 bits computer. And say doesn't support ubuntu 11.04. 

I have no intention to change or downgrade my OS to 32 bits, because I have 8GB RAM which 64 bits allow me to working with this memory. (32 bits can detect my 8GB RAM???  heard that 32 bit can support up to 4GB, right?)

i had try enforce the driver install in 64 bits architecture, but it doesn't work at all........

I still need to switch to my window 7 if I need to use the broadband....initially i dun wish to switch. 
because my primary OS is ubuntu 11.04 64 bits.

---

### Post by lkjoel on 2011-10-11
Could you run the Network Info Script (in my signature), and attach the generated file?

---

### Post by daveloh on 2011-10-12
> **lkjoel said:**
> Could you run the Network Info Script (in my signature), and attach the generated file?

with ur scripts i found information about the hardware as below:

> Bus 002 Device 007: ID 07d1:7e11 D-Link System 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x07d1 D-Link System
  idProduct          0x7e11 
  bcdDevice            0.00
  iManufacturer           3 D-Link,Incorporated
  iProduct                2 D-Link WCDMA Technologies MSM
  iSerial                 4 MF102DDLKD010000
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          108
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          1 D-Link Configuration
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
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
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
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
        bEndpointAddress     0x83  EP 3 IN
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
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               5
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
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

---

### Post by lkjoel on 2011-10-12
OK, it recognizes it, but could you attach the generated file? That will give me much more information on how to proceed.

---

### Post by daveloh on 2011-10-12
> **lkjoel said:**
> OK, it recognizes it, but could you attach the generated file? That will give me much more information on how to proceed.

Here u go~~~

---

### Post by lkjoel on 2011-10-13
Do you have a wireless card/device apart from the DWM-152?

---

### Post by daveloh on 2011-10-29
> **lkjoel said:**
> Do you have a wireless card/device apart from the DWM-152?

yes~~dell build-in Wifi card

---

### Post by lkjoel on 2011-10-30
OK, I'm not getting this. Try getting an Ubuntu 11.10 LiveCD, and see if it works there.

---

