---
title: "HP WebCam HD-4110"
date: 2012-10-04
forum: Multimedia Software
---

### Post by squaregoldfish on 2012-10-04
Hi,

Does anyone have any experience of using the HP WebCam HD-4110 with linux? I've looked in all the usual places and haven't come up with a definitive answer.

Thanks,
Steve.

---

### Post by jpnielzen on 2013-02-04
It works in ubuntu 12.10

lsusb

[ 620.316103] usb 2-1: >new high-speed USB device number 7 using ehci_hcd
[ 620.695462] usb 2-1: >New USB device found, idVendor=03f0, idProduct=9207
[ 620.695472] usb 2-1: >New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 620.695480] usb 2-1: >Product: HP Webcam HD-4110
[ 620.695486] usb 2-1: >Manufacturer: HP
[ 621.002484] Linux video capture interface: v2.00
[ 621.143280] usbcore: registered new interface driver snd-usb-audio
[ 621.143483] uvcvideo: Found UVC 1.00 device HP Webcam HD-4110 (03f0:9207)
[ 621.163496] input: HP Webcam HD-4110 as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0/input/input10
[ 621.163685] usbcore: registered new interface driver uvcvideo
[ 621.163690] USB Video Class driver (1.1.1)

---

