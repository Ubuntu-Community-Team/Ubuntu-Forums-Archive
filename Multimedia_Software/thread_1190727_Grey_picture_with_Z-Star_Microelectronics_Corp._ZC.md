---
title: "Grey picture with Z-Star Microelectronics Corp. ZC0303 WebCam"
date: 2009-06-18
forum: Multimedia Software
---

### Post by Hans Huckebein on 2009-06-18
Hi,
I'm using Kubuntu 8.04 and the above mentioned webcam.

lsusb gives
0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam

This is the dmesg output
[  601.349419] usb 3-2: USB disconnect, address 2
[  603.589390] usb 3-2: new full speed USB device using uhci_hcd and address 3
[  603.759874] usb 3-2: configuration #1 chosen from 1 choice
[  603.764603] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(ZC3XX)


/dev/video0 exists, but skype and camorama show only a grey picture. This cam seems to work for almost everyone out of the box, so google isn't getting me anywhere. Any hints?

---

