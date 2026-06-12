---
title: "Logitech Quickcam Notebook Very dark"
date: 2007-01-10
forum: Multimedia &amp; Video
---

### Post by TheFifth on 2007-01-10
Hi all,

After much messing around I've managed to get my Quickcam Notebook (046d:08ae) working in Edgy.  The problem I have is that the picture is so dark it's almost unusable in anything but very bright light.

According to Kopete it is using Input ZC301-2 and changing the brightness and contrast has very little effect.

When plugged in dmesg lists:

> [17183585.060000] usb 2-1: new full speed USB device using uhci_hcd and address 3
[17183585.264000] usb 2-1: configuration #1 chosen from 1 choice
[17183585.268000] /home/richard/spca5xx-20060501/drivers/usb/spca5xx.c: USB SPCA5XX camera found. Logitech QC for Notebooks 
[17183585.268000] /home/richard/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_probe:5480] Camera type JPEG 
[17183585.620000] /home/richard/spca5xx-20060501/drivers/usb/zc3xx.h: [zc3xx_config:543] Find Sensor PAS202BCB
[17183585.624000] /home/richard/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_getcapability:1765] maxw 640 maxh 480 minw 176 minh 144

I've tried using setpwc and dov4l to change the setting but to no avail.

Anyone got any idea of how to change the image quality of this camera?

---

### Post by adiboy on 2007-06-19
i am having the same problem is any one knows how to solv this problem.

---

