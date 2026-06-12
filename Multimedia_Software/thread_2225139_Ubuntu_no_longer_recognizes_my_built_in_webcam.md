---
title: "Ubuntu no longer recognizes my built in webcam"
date: 2014-05-20
forum: Multimedia Software
---

### Post by jacobvisick on 2014-05-20
So I know that in 13.10 my webcam was accessible, but just now I tried accessing it both with Cheese and guvcview and neither could open it. I know that it's being recognized on boot, because when I look at the dmesg output, I get this:

```
[   10.540011] usb 1-4: USB disconnect, device number 2[   10.810297] usb 1-4: new full-speed USB device number 10 using xhci_hcd
[   10.890799] uvcvideo: Found UVC 1.00 device USB2.0 UVC HD Webcam (13d3:5188)
[   10.896027] input: USB2.0 UVC HD Webcam as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/input/input19
[   10.896201] usbcore: registered new interface driver uvcvideo
[   10.896204] USB Video Class driver (1.1.1)

```

I've tried updating libv4l, and that make any difference. What can I do?

I tagged the thread as UbuntuGnome because that's what I'm running, but I can only assume it's the same for other variants as well.

---

