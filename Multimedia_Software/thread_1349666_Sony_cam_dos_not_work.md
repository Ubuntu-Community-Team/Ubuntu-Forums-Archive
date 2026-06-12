---
title: "Sony cam dos not work"
date: 2009-12-08
forum: Multimedia Software
---

### Post by sceletor1 on 2009-12-08
I have an HD camera through the USB to be connected. 
Linux sees the device but not entirely. 
If I do lsusb I get this in terminal see: 
Bus 002 Device 003: ID 0425:0101 Motorola Semiconductors HK, Ltd G-Tech Wireless Mouse & Keyboard 
Bus 002 Device 002: ID 046d: c50e Logitech, Inc.. MX-1000 Cordless Mouse Receiver 
Bus 002 Device 001: ID 1d6b: 0001 Linux Foundation 1.1 root hub 
Bus 001 Device 008: ID 054c: 02af Sony Corp.. Handy-cam DCR-DVD306E 
Bus 001 Device 005: ID 0bf8: 100F Fujitsu Siemens Computers 
Bus 001 Device 004: ID 05e3: 0710 Genesys Logic, Inc.. USB 2.0 33-in-1 Card Reader 
Bus 001 Device 001: ID 1d6b: 0002 Linux Foundation 2.0 root hub 

As you can see, Linux sees the camera here, but he can not connect with the camera. 
In nautilus I see the camera can not stand. 
The strange thing is that he is very now and again and then I suddenly makes the files of the dvdtje pick. 
've Already seen something about V4L2-dv but I can not find in synaptic. 
All kind of other versions do, do not know what I should have preccies. 
Did they even plug-in installed: 

Portable Windows Library Video Plugin for Video4Linux v2: 
This package contains the pwlib plugin for usage with Video4Linux v2 
devices. Install this package, if you want to use a video device 
that is not attached to FireWire. 

but this has not helped. 

Get the following to see if the camera is at: lsmod | grep usb 
usb_storage 52,544 
And cat / var / log / messages | grep usb 
 kernel: [4549.739245] usb 1-3: USB disconnect, address 3 
Arjan Nov 25 20:07:19 laptop kernel: [6212.720084] usb 1-3: new high speed USB device using ehci_hcd and address 4 
Arjan Nov 25 20:07:19 laptop kernel: [6212.853152] usb 1-3: configuration # 1 chosen from 1 choice 
  
Has anyone a solution? 

Gr, 

Arjan 
  
  
Has anyone a solution? 

Gr, 

Arjan

---

