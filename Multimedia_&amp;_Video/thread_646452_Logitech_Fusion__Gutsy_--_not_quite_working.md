---
title: "Logitech Fusion / Gutsy -- not quite working"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by ebstauffer on 2007-12-21
Recently installed Gutsy from scratch as upgrade failed miserably. I dont recall explicitly installing uvc drivers but they seem to be installed. Output which may be helpful-

dmesg:
[PHP]
[82161.226783] Linux video capture interface: v2.00
[93657.638593] usb 5-2: new high speed USB device using ehci_hcd and address 4
[93657.947321] usb 5-2: configuration #1 chosen from 1 choice
[93659.970315] 4:3:3: cannot set freq 16000 to ep 0x86
[93661.966721] usbcore: registered new interface driver snd-usb-audio
[93661.966732] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c1)
[93661.983821] usbcore: registered new interface driver uvcvideo
[93661.984023] USB Video Class driver (v0.1.0)
[94156.460752] uvcvideo: Failed to query (131) UVC control 1 (unit 0) : -32 (exp. 26).
[94157.068738] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -32 (exp. 26).
[94158.986225] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[/PHP]

lsusb:
[PHP]Bus 005 Device 004: ID 046d:08c1 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 005: ID 046d:c043 Logitech, Inc. 
Bus 003 Device 004: ID 045e:00db Microsoft Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  [/PHP]
046d:08c1 is cam, second is mouse, third is MS keyboard (I like their usb keyboard!)

caminfo:
[PHP]CVideoDeviceInput: Warning: no channel info available.
Detected 1 Video4Linux devices.
Device node      : /dev/video0
Name of device   : "UVC Camera (046d:08c1)"
Minimum size     : 48x32
Current size     : 0x0
Maximum size     : 0x0
Video inputs     : 1
 Input 0
  Name             : "(null)"
  Type             : Unknown
  Audio            : no
  Tuners           : 0
Audio inputs     : 0
[/PHP]

Any help would be greatly appreciated

---

