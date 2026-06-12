---
title: "Phillips ToUCam"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by magikx21 on 2007-12-30
I have a Phillips ToUCam XS PCVC720K/17, When I plug it in the light on it turns on but when I try to open Camorama I get the error: Could not connect to video device (/dev/video0). Please check connection

Here is my dmesg output:
```
[ 2575.785636] /home/mxm/ov51x-jpeg-1.5.4/ov51x-jpeg-core.c: USB OV518 video dev                         ice found
[ 2575.786938] /home/mxm/ov51x-jpeg-1.5.4/ov51x-jpeg-core.c: Device revision 1
[ 2575.799917] /home/mxm/ov51x-jpeg-1.5.4/ov51x-jpeg-core.c: Compression require                         d with OV518...enabling
[ 2578.154256] /home/mxm/ov51x-jpeg-1.5.4/ov51x-jpeg-core.c: WARNING: Sensor is                          an OV66308. Your camera may have
[ 2578.154267] /home/mxm/ov51x-jpeg-1.5.4/ov51x-jpeg-core.c: been misdetected in                          previous driver versions. Please
[ 2578.154273] /home/mxm/ov51x-jpeg-1.5.4/ov51x-jpeg-core.c: report this to Mark                         .
[ 2578.599557] /home/mxm/ov51x-jpeg-1.5.4/ov51x-jpeg-core.c: Device at usb-0000:                         00:10.0-1 registered to minor 1
[ 2578.599799] usbcore: registered new interface driver ov51x
[ 2578.599920] /home/mxm/ov51x-jpeg-1.5.4/ov51x-jpeg-core.c: 1.5.4 : ov51x USB C                         amera Driver
[ 2578.742381] usbcore: registered new interface driver ov511
[ 2578.742525] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/bui                         ld-generic/media/ov511/ov511.c: v1.64 for Linux 2.5 : ov511 USB Camera Driver

```

Does anyone know how I can get this working?

---

### Post by magikx21 on 2007-12-31
Okay I got the camera working in camstream. However when I open Camorama it loads my TV Tuner since it is /dev/video0. Is there a way to make Camorama load my webcam at /dev/video1?

---

