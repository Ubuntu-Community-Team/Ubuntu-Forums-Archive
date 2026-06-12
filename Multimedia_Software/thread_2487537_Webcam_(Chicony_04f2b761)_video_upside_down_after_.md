---
title: "Webcam (Chicony 04f2:b761) video upside down after suspend 22.04LTS"
date: 2023-06-07
forum: Multimedia Software
---

### Post by goose1123 on 2023-06-07
Integrated webcam (Chicony 04f2:b761 webcam using uvcvideo driver) video in ThinkPad T14s Gen 3 is upside down (vertically flipped) after suspend. It is the right way up after restart. Tested on Cheese, Zoom and Firefox, all behave this way. I am using  Xubuntu 22.04.2 LTS but also tested on Ubuntu 22.04.2 LTS via bootable  USB and got the same problem (thus the all variants tag, was not sure what best to put).

Have unsuccessfully tried:

* restarting webcam (via `sudo rmmod uvcvideo` then `sudo modprobe uvcvideo`)
* resetting webcam device
* `LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so` and `LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so`.

I think it is a driver issue and would like to potentially file a bug  report. Is there a way to confirm that it is before I do this? This gives a  link to the driver code: [https://linux-hardware.org/?id=usb:04f2-b761](https://linux-hardware.org/?id=usb:04f2-b761) . I noticed that my specific webcam is not listed in the code, is this a problem?

Thank you for any help!


Webcam details:

```
             *-usb:1
                   description: Video
                   product: Integrated Camera: Integrated C
                   vendor: Chicony Electronics Co.,Ltd.
                   physical id: 4
                   bus info: usb@3:4
                   logical name: input14
                   logical name: /dev/input/event9
                   version: 27.74
                   serial: 0001
                   capabilities: usb-2.01 usb
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
```

and from startup `dmesg`:

```
[    2.211395] usb 3-4: New USB device found, idVendor=04f2, idProduct=b761, bcdDevice=27.74
[    2.211398] usb 3-4: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    2.211400] usb 3-4: Product: Integrated Camera
[    2.211401] usb 3-4: Manufacturer: Chicony Electronics Co.,Ltd.
[    2.211402] usb 3-4: SerialNumber: 0001
```

I have posted more details here: [https://askubuntu.com/questions/1470994/thinkpad-webcam-video-inverted-upside-down-after-suspend-22-04-2-lts](https://askubuntu.com/questions/1470994/thinkpad-webcam-video-inverted-upside-down-after-suspend-22-04-2-lts)

---

