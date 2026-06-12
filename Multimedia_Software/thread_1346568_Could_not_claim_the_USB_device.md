---
title: "Could not claim the USB device"
date: 2009-12-05
forum: Multimedia Software
---

### Post by frisket on 2009-12-05
I'm running 9.10 and I wanted to use my old Kodak EZ200, so I installed gphoto2 and plugged it in.

gphoto2 --auto-detect correctly reports Kodak "EZ200 usb:" but any attempt to use it returns this error 53 "Could not claim the USB device'. 

lsusb reports:

Bus 004 Device 007: ID 040a:0300 Kodak Co. EZ-200
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

dmesg says

[   88.376017] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   88.569057] usb 4-1: configuration #1 chosen from 1 choice
[   88.823211] Linux video capture interface: v2.00
[   88.875385] gspca: main v2.6.0 registered
[   88.971137] usbcore: registered new interface driver spca500
[   88.971144] spca500: registered

and tail /var/log/messages says

Dec  5 13:14:41 adam kernel: [ 5934.080034] usb 4-1: new full speed USB device using uhci_hcd and address 3
Dec  5 13:14:41 adam kernel: [ 5934.273103] usb 4-1: configuration #1 chosen from 1 choice
Dec  5 13:14:41 adam kernel: [ 5934.276060] gspca: probing 040a:0300
Dec  5 13:14:41 adam kernel: [ 5934.276129] gspca: probe ok
Dec  5 13:14:41 adam kernel: [ 5934.276186] gspca: probing 040a:0300
Dec  5 13:14:41 adam kernel: [ 5934.852324] gspca: disconnect complete

There are some threads here about this error but none of them seem to be later than 2007 and they refer to a file (/etc/udev/rules.d/45-libgphoto2.rules) which does not exist on my system. The claim seems to be that libgphoto has/had a bug which prevented it claiming USB cameras.

Is there some additional package I need to install to overcome this?

P

---

