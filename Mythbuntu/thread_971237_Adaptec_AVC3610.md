---
title: "Adaptec AVC3610"
date: 2008-11-04
forum: Mythbuntu
---

### Post by NetRider on 2008-11-04
This is a usb unit with remote and dual tuners.  Just wondering if anyone got this to work with MYTHBUNTU?

lsusb resuts:
sudo lsusb -v -s 005

Bus 005 Device 005: ID 03f3:0094 Adaptec, Inc. eHome Infrared Receiver
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        16
  idVendor           0x03f3 Adaptec, Inc.
  idProduct          0x0094 eHome Infrared Receiver
  bcdDevice            0.00
  iManufacturer           1 Adaptec
  iProduct                2 eHome Infrared Transceiver
  iSerial                 3 AD000mf8
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
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
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               0
Device Status:     0x0001
  Self Powered

Thanks in advance...

---

### Post by NetRider on 2008-11-06
oops, that was only the infared receiver... here are the rest
lusb results:
Bus 005 Device 005: ID 03f3:0094 Adaptec, Inc. eHome Infrared Receiver
Bus 005 Device 004: ID 03f3:0090 Adaptec, Inc. 
Bus 005 Device 002: ID 03f3:0044 Adaptec, Inc. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

dmesg results: 
[  677.152039] usb 5-5: new high speed USB device using ehci_hcd and address 6
[  677.285657] usb 5-5: configuration #1 chosen from 1 choice
[  677.286817] hub 5-5:1.0: USB hub found
[  677.287269] hub 5-5:1.0: 3 ports detected
[  677.584163] usb 5-5.1: new high speed USB device using ehci_hcd and address 7
[  677.692717] usb 5-5.1: configuration #1 chosen from 1 choice
[  677.768642] usb 5-5.3: new full speed USB device using ehci_hcd and address 8
[  677.879105] usb 5-5.3: configuration #1 chosen from 1 choice

I'm trying this on a mythbuntu 8.10 box.  Suggestions? Ideas?  Thanks again!

---

### Post by zdea on 2008-11-14
I have this as well and am investigating it. However everything I've read online suggests that nobody cares about this model as it is not widely enough owned. Therefor I may be stuck with WMCE indefinately with it. Very lame as MS will never allow me to stream live video to other pcs... apparantly a feature they want to reserve for there crappy media center extenders.

---

### Post by psysmic on 2009-01-31
I kept finding this thread when looking to find the solution.  Here's what worked for me:  [http://ubuntuforums.org/showthread.php?p=6652648#post6652648](http://ubuntuforums.org/showthread.php?p=6652648#post6652648) for the IR Remote

Props to Lem

---

### Post by fluffd on 2009-12-08
Just to let anyone/everyone know about this tuner from adaptec.
It is "supported" chip wise. I opened mine up after, I dunno, 4 years. Its covered under the pvrusb2 driver. It has to be added in device wise, i've been working on it. the developer hangs out in #pvrusb2,#linuxtv,#v4l on freenode.

---

