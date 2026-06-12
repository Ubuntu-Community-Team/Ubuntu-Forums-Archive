---
title: "How to fix for UVC Camera: USB disconnect"
date: 2012-11-29
forum: Multimedia Software
---

### Post by whenthewestwaswon on 2012-11-29
In dmesg I get multiple times my internal non-working webcam as a USB disconnect. See below.

Now I guess this may be related to the fact that my webcam is not working, in xubuntu 12.04; mostly something like Device Not Found while it is being recognised that there is a USB2.0 Camera available.

Question:
Does anyone know how I can fix this? Thanks.  

[  238.284469] usb 1-8: USB disconnect, device number 3
[  238.428080] usb 1-8: new high-speed USB device number 4 using ehci_hcd
[  238.702938] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (05e3:0505)
[  238.841289] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input11
[  250.616497] usb 1-8: USB disconnect, device number 4
[  250.760136] usb 1-8: new high-speed USB device number 5 using ehci_hcd
[  251.037024] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (05e3:0505)
[  251.175427] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input12
[  261.872380] usb 1-8: USB disconnect, device number 5
[  262.016085] usb 1-8: new high-speed USB device number 6 using ehci_hcd
[  262.292016] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (05e3:0505)
[  262.430606] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input13
[  272.716364] usb 1-8: USB disconnect, device number 6
[  272.828496] usb 1-8: new high-speed USB device number 7 using ehci_hcd
[  273.102825] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (05e3:0505)
[  273.243821] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input14
[  287.944403] usb 1-8: USB disconnect, device number 7
[  288.056095] usb 1-8: new high-speed USB device number 8 using ehci_hcd
[  288.331257] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (05e3:0505)
[  288.469601] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input15
[  304.344428] usb 1-8: USB disconnect, device number 8
[  304.492080] usb 1-8: new high-speed USB device number 9 using ehci_hcd
[  304.767547] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (05e3:0505)
[  304.906304] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input16
[  312.916436] usb 1-8: USB disconnect, device number 9
[  313.028096] usb 1-8: new high-speed USB device number 10 using ehci_hcd
[  313.303454] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (05e3:0505)
[  313.442663] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input17
[  323.072410] usb 1-8: USB disconnect, device number 10
[  323.212093] usb 1-8: new high-speed USB device number 11 using ehci_hcd
[  323.487941] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (05e3:0505)
[  323.627017] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input18
[  752.204383] usb 1-8: USB disconnect, device number 11
[  752.344078] usb 1-8: new high-speed USB device number 12 using ehci_hcd
[  752.620938] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (05e3:0505)
[  752.759450] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input19
[  769.388594] usb 1-8: USB disconnect, device number 12
[  769.528159] usb 1-8: new high-speed USB device number 13 using ehci_hcd
[  769.802963] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (05e3:0505)
[  769.941090] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input20

---

### Post by Raff1 on 2013-02-21
I am getting the exact same error messages on Ubuntu 12.04. However, my problem is with a functioning integrated webcam.

When on Skype or other video calls my camera (indicated with a green LED next to it) occasionally turns off and on for a brief moment with adjusted brightness or screen ratio. I have never thought much about it. In rare cases, my camera failed to reconnect/turn on again and I had to do it manually.

However, this has happened more and more often the last couple of weeks. by now, the camera lasts for about 3 minutes if I am lucky, and about 10 seconds if my PC is in a bad mood.

I have seen a lot of variants of this problem when searching the forums, but none of them made me able to get anywhere. If OP could change the tag to [all variants] it would be appreciated :p

---

