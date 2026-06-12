---
title: "Module for eb1a:5052 usb-webcam?"
date: 2010-10-15
forum: Multimedia Software
---

### Post by mvykos on 2010-10-15
Hi,

I've been struggling for days trying to get my webcam to work.

I've got a usb eb1a:5052 webcam, as lsusb shows:

```
Bus 001 Device 007: ID eb1a:5052 eMPIA Technology, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0xeb1a eMPIA Technology, Inc.
  idProduct          0x5052 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 USB 2750 Camera
  iSerial                 0 
  bNumConfigurations      1

(cut off the rest)

```I don't know if the kernel version matters, but I'm running 2.6.32-25-generic.
I've got no /dev/video0.
Cheese reports just that, "no device found".

I found this link [http://www.linuxtv.org/wiki/index.php/Em28xx_devices](http://www.linuxtv.org/wiki/index.php/Em28xx_devices) which indicates the em28xx module for some eb1a devices.

The module was already installed, so at first I just tried loading the module, but it didn't work. So I followed the instructions on that link to compile (a possibily new version of) em28xx. Still it didn't work.

When I turn on/off the camera, dmesg shows:

```
[ 1751.032478] usb 1-5: USB disconnect, address 8
[ 1751.400080] usb 1-5: new high speed USB device using ehci_hcd and address 9
[ 1751.535761] usb 1-5: configuration #1 chosen from 1 choice

```If the modue was correct, it should be loaded as the camera goes up, isn't it?
Is the module the one responsible for creating /dev/video0 ?

Does anyone have a clue if em28xx is the right module?

Thanks!

---

