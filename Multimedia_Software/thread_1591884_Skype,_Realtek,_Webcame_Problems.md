---
title: "Skype, Realtek, Webcame Problems"
date: 2010-10-10
forum: Multimedia Software
---

### Post by jubantu on 2010-10-10
Hi,

I have problems with my webcam Logitech Quickcam E3500. Everytime I connect it via USB I loose my Wireless Internet Connetion....

```
lsusb

Bus 001 Device 002: ID 046d:09a4 Logitech, Inc. QuickCam E 3500
```

```
lsmod | grep videodev

videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev

```

After I restart my Laptop the wireless internet connection is working again. If I plug the camera in, the wireless is gone. How can I get the camera and my wireless to work?

Thanks in advance...

---

