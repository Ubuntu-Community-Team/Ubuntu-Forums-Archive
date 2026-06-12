---
title: "Ezcap USB 2.0 Video Capture"
date: 2013-07-03
forum: Multimedia Software
---

### Post by peterthebike on 2013-07-03
I have an Ezcap USB 2.0 Video Capture that I am using with a webcam. With Windows 7 it is working OK.

Using VLC I have not been able to see the webcam, only the inbuilt webcam in my laptop. I have tried the suggestion of using plughw:1,0 as the device name but that did not work.

The output from dmesg is:
```
[ 1349.848840] usb 1-1.1: new high-speed USB device number 5 using ehci-pci
[ 1349.947697] usb 1-1.1: New USB device found, idVendor=eb1a, idProduct=5124
[ 1349.947706] usb 1-1.1: New USB device strings: Mfr=0, Product=1, SerialNumber=2
[ 1349.947713] usb 1-1.1: Product: USB VIDBOX FW Audio
[ 1349.947718] usb 1-1.1: SerialNumber: USB2.0 VIDBOX FW
```

Can anyone suggest what to do please?

---

