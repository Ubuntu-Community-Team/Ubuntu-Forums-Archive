---
title: "Creative Webcam 3 Problems"
date: 2009-10-15
forum: Multimedia Software
---

### Post by Sethi78 on 2009-10-15
Hi guys! I'm trying to connect my Creative Webcam 3, but I've got some problems:
I install webcam driver with "EasyCam2", but after the connection of the camera:[I][FONT=Verdana]

sethi@imothep-ubuntu:~$ dmesg | tail
[70070.328292] usb 2-4.3: new full speed USB device using ehci_hcd and address 11
[70070.420871] usb 2-4.3: configuration #1 chosen from 1 choice
[70070.421064] ov511: USB OV511 video device found
[70070.421158] ov511: model: Creative Labs WebCam 3
[70070.594661] ov511: Sensor is an OV7610
[70070.624600] ov511: Device at usb-0000:00:1d.7-4.3 registered to minor 0

sethi@imothep-ubuntu:~$ lsusb
Bus 002 Device 011: ID 05a9:0511 OmniVision Technologies, Inc. OV511 WebCam
Bus 002 Device 009: ID 07ff:00ff  
Bus 002 Device 008: ID 0951:1607 Kingston Technology Data Traveler 2.0
Bus 002 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

sethi@imothep-ubuntu:~$ ls -l /dev/video*
crw-rw---- 1 root video 81, 0 2009-10-15 16:42 /dev/video0[/FONT][/I]

Everything looks like ok, but when I start "chees", "camorama" or any other program... They give me this error: "could not connect to video device".

---

