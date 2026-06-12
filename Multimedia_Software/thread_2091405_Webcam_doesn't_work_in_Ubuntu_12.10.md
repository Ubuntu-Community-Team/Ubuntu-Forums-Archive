---
title: "Webcam doesn't work in Ubuntu 12.10"
date: 2012-12-05
forum: Multimedia Software
---

### Post by kzhi on 2012-12-05
I have Gembird cam68ut. On my Ubuntu 12.10 it shows black screen in cheese and guvcview. I tested it in win7, it works fine.

Here what I found:

[LIST]
[*]It is a uvc compliant camera, I checked on the [site]("http://www.ideasonboard.org/uvc/#devices"): 18ec:3299 USB 2.0 PC Camera (model number QC3231) ArkMicro
[*]This webcam is report by lsusb: Bus 001 Device 004: ID 18ec:3299 Arkmicro Technologies Inc.
[*]Here is the output of **dmesg | tail**:

```
uvcvideo: Found UVC 1.00 device USB2.0 PC CAMERA (18ec:3299)
uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
input: USB2.0 PC CAMERA as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input17
usbcore: registered new interface driver uvcvideo
USB Video Class driver (1.1.1)
```
[*]When I run **cheese** (or **guvcview**), here what I get in terminal:
```
libv4l2: error turning on stream: No space left on device
(cheese:11797): cheese-WARNING **: Internal data flow error.
```
[*]I tried it on different usb slots with the same results
[*]The Webcam's microphone works, I can record audio with it
[/LIST]
Guys, any thoughts on what can be done to make it work?

---

### Post by kzhi on 2012-12-05
It started to work on another machine with the same xubuntu 12.10 without any tricks. ;)
I don't know why, may be not enough usb bandwidth on my home pc.

---

