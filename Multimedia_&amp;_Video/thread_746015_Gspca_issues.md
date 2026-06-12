---
title: "Gspca issues"
date: 2008-04-05
forum: Multimedia &amp; Video
---

### Post by scamelscrud on 2008-04-05
Hi,

my problem is that the camera is integrated into the monitor. Monitor has a hub inside, so camera is actually connected via a hub.

Here is lsusb:
```
Bus 004 Device 013: ID 0ac8:0302 Z-Star Microelectronics Corp. ZC0302 WebCam
Bus 004 Device 010: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

dmesg output:
```
[ 2340.619172] usb 4-3.4: new full speed USB device using ehci_hcd and address 13
[ 2340.712746] usb 4-3.4: configuration #1 chosen from 1 choice
[ 2340.713283] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(ZC3XX) 
[ 2342.554444] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
```

As you can see the device is connected using ehci_hcd. And it's a problem. Because with ehci_hcd the image is flipped and there are messages with "-28" code in dmesg. I guess the usb 2.0 hub in monitor is causing connection using ehci_hcd.

If I unplug the camera and connect it directly to usb port it's working fine! And in this case it uses uhci_hcd. Another solution is to unload ehci_hcd before using the camera and it will use uhci_hcd.

So I cannot use the camera, when it's on my monitor. But it was designed to be on monitor :)

Is there any way I can implement an exception for the camera device to use uchi_hcd instead of ehci_hcd ? Or some patches to get this working on ehci_hcd too?

---

