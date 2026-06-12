---
title: "Logiteck QuickCam E35000,Skype, video doesn't work!"
date: 2012-04-21
forum: Multimedia Software
---

### Post by enricox on 2012-04-21
I am using Ubuntu 10.04.4 32 bit with skype 2.2.0.35.The problem is the video.It is black when I try to use the webcam.I got the library libv4l in /sbin.
 I found this trick on Internet:
 LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
 but it doesn't work!
 When I stop the skype process I receive:
 
libv4l2: error dequeuing buf: Invalid argument.
 Just to give u an idea:
 lsusb:
Bus 002 Device 002: ID 046d:09a4 Logitech, Inc. QuickCam E 3500
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 dmesg | grep usb:
[    0.204163] usbcore: registered new interface driver usbfs
[    0.204178] usbcore: registered new interface driver hub
[    0.204210] usbcore: registered new device driver usb
[    0.330222] usb usb1: configuration #1 chosen from 1 choice
[    0.381852] usb usb2: configuration #1 chosen from 1 choice
[    0.382237] usb usb3: configuration #1 chosen from 1 choice
[    0.382521] usb usb4: configuration #1 chosen from 1 choice
[    0.382777] usb usb5: configuration #1 chosen from 1 choice
[    0.383032] usb usb6: configuration #1 chosen from 1 choice
[    0.383280] usb usb7: configuration #1 chosen from 1 choice
[    0.383536] usb usb8: configuration #1 chosen from 1 choice
[    0.703593] usb 2-3: new high speed USB device using ehci_hcd and address 2
[    0.948506] usb 2-3: configuration #1 chosen from 1 choice
[    1.059549] usb 2-5: new high speed USB device using ehci_hcd and address 3
[    1.180970] usb 2-5: configuration #1 chosen from 1 choice
[    1.356613] usbcore: registered new interface driver usb-storage
[    1.356623] usb-storage: device found at 3
[    1.356625] usb-storage: waiting for device to settle before scanning
[    4.983654] input: UVC Camera (046d:09a4) as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/input/input4
[    4.983723] usbcore: registered new interface driver uvcvideo
[    5.512024] usbcore: registered new interface driver snd-usb-audio
[    6.360202] usb-storage: device scan complete
locate v4l1compat.so:
/usr/lib/libv4l/v4l1compat.so
 Any suggestions?

 Thanks!

---

