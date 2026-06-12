---
title: "Capture card &quot;blocks access&quot; to webcam?"
date: 2008-12-16
forum: Multimedia Software
---

### Post by Jose Catre-Vandis on 2008-12-16
Running xubuntu 8.10

I have a Logitech Quickcam Express
```
Bus 002 Device 002: ID 046d:0870 Logitech, Inc. QuickCam Express
```
and an ASUS p7131 TV capture card
```
01:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
	Subsystem: ASUSTeK Computer Inc. Device 4857
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at e9000000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134
```

The capture card usually occupies /dev/video0

When I plug in the webcam the drivers are loaded;
```
[17056.528042] usb 2-2: new full speed USB device using ohci_hcd and address 2
[17056.742336] usb 2-2: configuration #1 chosen from 1 choice
[17056.978899] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[17056.978907] quickcam: Kernel:2.6.27-7-generic bus:2 class:FF subclass:FF vendor:046D product:0870
[17057.001087] quickcam: Sensor HDCS-1020 detected
[17057.007359] quickcam: Registered device: /dev/video1
[17057.007391] usbcore: registered new interface driver quickcam
```

but none of the test programs like Cheese or Skype can access it on /dev/video1. if i boot up with webcam attached, it will be assigned /dev/video0 but still not found in these programs.

Anyway I can reconfigure, switch things around or temporarily disable the capture card to see if I can get the webcam working?

---

