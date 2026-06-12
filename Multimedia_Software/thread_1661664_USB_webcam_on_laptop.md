---
title: "USB webcam on laptop"
date: 2011-01-07
forum: Multimedia Software
---

### Post by detectiveinspekta on 2011-01-07
I have a USB webcam I found, am trying to get it working under linux, didn't work on my server as its got USB 2.0 and I'm sure the webcam doesnt support USB2.0.

The laptop I am trying it out on has a internal webcam and I think its interfering with the USB camera.

In dev there is video0 and video1, both are for the internal webcam as I'v tried with streamer to grab images.


```

[  653.402224] usb 1-5: USB disconnect, address 11
[  653.672045] usb 1-5: new high speed USB device using ehci_hcd and address 12
[  653.864498] usb 1-5: unable to read config index 0 descriptor/all
[  653.864505] usb 1-5: can't read configurations, error -71
[  653.980133] usb 1-5: new high speed USB device using ehci_hcd and address 13
[  654.384428] hub 1-0:1.0: unable to enumerate USB device on port 5
[  654.652167] usb 4-1: new full speed USB device using uhci_hcd and address 2
[  654.720207] hub 4-0:1.0: unable to enumerate USB device on port 1
[  655.128151] usb 4-1: new full speed USB device using uhci_hcd and address 3
[  655.272200] usb 4-1: not running at top speed; connect to a high speed hub
[  655.359324] usb 4-1: configuration #1 chosen from 1 choice
[  655.369208] uvcvideo: Found UVC 1.00 device Sirius USB2.0 Camera (0ac8:3330)
[  655.375351] input: Sirius USB2.0 Camera as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input16


```
```

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0ac8:3330 Z-Star Microelectronics Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse

```

---

### Post by no2498 on 2011-01-07
set the cam you would like to use here

click system, preferences
go down the list to multimedia systems selector, start it click video
try v4l and v4l2 click the bottom test button for each 1

---

