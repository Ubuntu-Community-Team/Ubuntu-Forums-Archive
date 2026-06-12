---
title: "Driver for Praktica / DXG USB Camcorder"
date: 2010-02-14
forum: Multimedia Software
---

### Post by steveh2009 on 2010-02-14
Hi

I was wondering if anyone could help me locate a suitable driver for my Praktica DVC50 camcorder to use it as a webcam.

When I check dmesg log after I have plugged it in, i can see that the camera is detected :-
[I][B][73819.592047] usb 3-2: new full speed USB device using uhci_hcd and address 3
[73819.731945] usb 3-2: not running at top speed; connect to a high speed hub
[73819.755094] usb 3-2: configuration #1 chosen from 1 choice[/B][/I]

When I check lsusb it shows as a DXG device :-
***Bus 003 Device 003: ID 0d64:0338 DXG Technology Corp.***

Any assistance in getting this to work with karmic would be great.
Thanks

---

### Post by sasaenator on 2010-04-27
I have the same problem with my praktica digital camera.Everything is all right when I plug it in as a mass storage device,but as a pc cam it doesn't work,even though it is listed in dmesg output.Praktica type is DCZ 8 VR,so it is not same as yours but I hope the driver or the problem is similar!Hope someone will help us :),or maybe it will work in Lucid!Here is my lsusb output(camera is also detected as DXG tech. corp.):

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0d64:0338 DXG Technology Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems)

---

