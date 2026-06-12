---
title: "Unable to install the D-link Wireless N 150 USB Adapter"
date: 2012-07-08
forum: Networking &amp; Wireless
---

### Post by simonyee on 2012-07-08
Hi,
I have been around Ubuntu for a long time but I have to admit this one have me stump.
ok I have this to show when I type it in
[HTML]user@user-945G:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 2001:3c17 D-Link Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/HTML]

user@user-945G:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Along the line I have get it to work through this site but after that I lost it.
ok Here is the question.
1. How to check what chipset does the wireless is using?
2. How to clear all the older chipset from working or detecting it?
3. Where and what to do first?

Oppss
I think I install the wrong kernel
uname -r
3.0.1-030001-generic
How then ?

Oppss again:--
Bus 001 Device 002: ID 2001:3c17 D-Link Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x2001 D-Link Corp.
  idProduct          0x3c17 
  bcdDevice            1.01
  iManufacturer           1 Ralink
  iProduct                2 11n Adapter
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           53
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
      bNumEndpoints           5
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


Please help me by step by step instruction.
Thanks
Simon Yee

---

### Post by praseodym on 2012-07-08
Hi,

first: install both files of the kernel headers for this kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.1-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.1-oneiric/)

Then the tools to compile (you may need them):

```
sudo apt-get install build-essential dkms
```


Which Ubuntuversion do you use? This chipset is supportet from module rt2800usb (latest kernels!).

[http://cateee.net/lkddb/web-lkddb/RT2800USB.html](http://cateee.net/lkddb/web-lkddb/RT2800USB.html)

> vendor: 2001 ("D-Link Corp."), product: 3c17

You may try a newer Ubuntu version or a newer kernel

---

### Post by simonyee on 2012-07-09
Hi,
Sorry to clarify I have version 10.10. so how to get the wireless to work on such an old system?
Thank you
Simon Yee

---

### Post by praseodym on 2012-07-09
10.10 is outdated and no longer supported. Try to update to 11.04 or a fresh install of 12.04

---

