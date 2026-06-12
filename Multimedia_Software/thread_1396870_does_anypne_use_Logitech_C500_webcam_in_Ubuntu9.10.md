---
title: "does anypne use Logitech C500 webcam in Ubuntu9.10 ?"
date: 2010-02-02
forum: Multimedia Software
---

### Post by eii on 2010-02-02
It seems to be recognized as follows:

mmm:~/modules/qc-usb$ lsusb
Bus 001 Device 002: ID 046d:0807 Logitech, Inc. 
mmm:~/modules/qc-usb$ dmesg | tail -20
[1117111.250016] usb 1-2: new high speed USB device using ehci_hcd and address 2
[1117111.568218] usb 1-2: configuration #1 chosen from 1 choice
[1117111.870728] Linux video capture interface: v2.00
[1117112.100407] usbcore: registered new interface driver snd-usb-audio
[1117112.100421] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0807)
[1117112.115509] input: UVC Camera (046d:0807) as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input6
[1117112.115557] usbcore: registered new interface driver uvcvideo
[1117112.115559] USB Video Class driver (v0.1.0)

But when I try to use camorama, it just says "Could not connect to video device (/dev/video0). Please check connection."
I added myself to video group.
Any ideas ?

mmm:~/modules/qc-usb$ ls -la /dev/video0 
crw-rw----+ 1 root video 81, 0 2010-02-02 09:18 /dev/video0

---

### Post by no2498 on 2010-02-05
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button

now get a program ( cheese and wxcam ) 1 of the 2 will see your cam

---

