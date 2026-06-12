---
title: "Mbox2 mini, Audacity, Ardour. not sure if its working or not :/"
date: 2014-04-26
forum: Multimedia Software
---

### Post by styrofoam-feet on 2014-04-26
So I installed Ubuntu Studio. Love it! My lexicon omega device works great!! but I cant tell if my mbox2 mini is working properly. Audacity registers that the mbox is there, but I cannot get a signal. The front usb light on the mbox is not on, or flickering or anything. I plugged the mbox into a windows box, and it too registered, but no light on the front. Phantom power is off. I did the [B]dmesg | grep -i . 
got this:

[/B]/2-3/2-3:1.0/input/input4
[   15.443234] usbcore: registered new interface driver uvcvideo
[   15.443237] USB Video Class driver (1.1.1)
[   15.657631] usbcore: registered new interface driver snd-usb-audio
[  231.704214] usb 6-1: USB disconnect, device number 2
[  249.886172] usb 6-1: new full-speed USB device number 3 using uhci_hcd
[  250.100562] usb 6-1: config 1 interface 2 has no altsetting 1
[  250.100570] usb 6-1: config 1 interface 3 has no altsetting 1
[  250.100574] usb 6-1: config 1 interface 4 has no altsetting 1
[  250.100578] usb 6-1: config 1 interface 5 has no altsetting 1
[  250.124538] usb 6-1: New USB device found, idVendor=0dba, idProduct=3000
[  250.124545] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=1
[  250.124550] usb 6-1: Product: Mbox 2 
[  250.124554] usb 6-1: Manufacturer: Digidesign
[  250.124559] usb 6-1: SerialNumber: Digidesign

Is that the info needed? Does this mean anything to anyone? Im still new to ubuntu and recording on linux and would really like to get my mbox working... any ideas? Thanks so much!

---

