---
title: "USB Webcam over network"
date: 2011-01-12
forum: Multimedia Software
---

### Post by allanvs on 2011-01-12
Good Day
 
I am busy going nuts here. I have a **Network USB 2.0 Server** from ARKView connected to it is a Logitech 1.3 megapixel webcam. Running Ubuntu 10.04
 
Is there a way i can connect to\mount the webcam and then view the stream from either VLC or RhythmBox or any other application that might work better?
 
I have installed usbip and when i try to connect using sudo usbip -x I.P. it fails.
 
Output of dmesg 
 
[14768.569373] usb 6-1: USB disconnect, address 2
[18583.604051] usb 2-3: new high speed USB device using ehci_hcd and address 6
[18583.852073] usb 2-3: configuration #1 chosen from 1 choice
[18584.458455] Linux video capture interface: v2.00
[18584.480357] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a1)
[18584.510460] input: UVC Camera (046d:09a1) as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/input/input13
[18584.510555] usbcore: registered new interface driver uvcvideo
[18584.511329] USB Video Class driver (v0.1.0)
[18584.540424] usbcore: registered new interface driver snd-usb-audio
[18704.040759] usb 2-3: USB disconnect, address 6
 
If anybody can help this would be great.
 
Thanks in advance.

---

