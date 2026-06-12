---
title: "spc1300nc webcam no /dev/video"
date: 2008-04-28
forum: Multimedia Software
---

### Post by LordTiggy on 2008-04-28
Hi,

I just bought a Philips SPC1300NC/00 webcam that is supposed to be working with uvc driver.

Camera is detected and driver loads perfectly but no /dev/video is created ... I hope anyone here can help me out :)

More info:

> ubuntu 2.6.15-51-server 

tiggy@gecko:~$ lsusb
Bus 005 Device 004: ID 0471:0331 Philips
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

tiggy@gecko:~$ lsmod | grep video
uvcvideo 62600 0
v4l1_compat 16132 1 uvcvideo
videodev 10752 1 uvcvideo
v4l2_common 7040 1 uvcvideo
usbcore 139140 6 uvcvideo,snd_usb_audio,snd_usb_lib,ehci_hcd,uhci_hcd

When probing uvcvideo i get:

tiggy@gecko:~$ sudo modprobe -v uvcvideo trace=15
insmod /lib/modules/2.6.15-51-server/kernel/drivers/media/video/v4l2-common.ko
insmod /lib/modules/2.6.15-51-server/kernel/drivers/media/video/videodev.ko
insmod /lib/modules/2.6.15-51-server/kernel/drivers/media/video/v4l1-compat.ko
insmod /lib/modules/2.6.15-51-server/kernel/ubuntu/media/usbvideo/uvcvideo.ko trace=15

dmesg shows:

tiggy@gecko:~$ dmesg
[42951421.940000] usbcore: deregistering driver uvcvideo
[42951427.970000] Linux video capture interface: v1.00
[42951427.980000] uvcvideo: Adding mapping Brightness to control 00000000-0000-0000-0000-000000000101/2.
[42951427.980000] uvcvideo: Adding mapping Contrast to control 00000000-0000-0000-0000-000000000101/3.
[42951427.980000] uvcvideo: Adding mapping Hue to control 00000000-0000-0000-0000-000000000101/6.
[42951427.980000] uvcvideo: Adding mapping Saturation to control 00000000-0000-0000-0000-000000000101/7.
[42951427.980000] uvcvideo: Adding mapping Sharpness to control 00000000-0000-0000-0000-000000000101/8.
[42951427.980000] uvcvideo: Adding mapping Gamma to control 00000000-0000-0000-0000-000000000101/9.
[42951427.980000] uvcvideo: Adding mapping Backlight Compensation to control 00000000-0000-0000-0000-000000000101/1.
[42951427.980000] uvcvideo: Adding mapping Gain to control 00000000-0000-0000-0000-000000000101/4.
[42951427.980000] uvcvideo: Adding mapping Power Line Frequency to control 00000000-0000-0000-0000-000000000101/5.
[42951427.980000] uvcvideo: Adding mapping Hue, Auto to control 00000000-0000-0000-0000-000000000101/16.
[42951427.980000] uvcvideo: Adding mapping Exposure, Auto to control 00000000-0000-0000-0000-000000000001/2.
[42951427.980000] uvcvideo: Adding mapping Exposure, Auto Priority to control 00000000-0000-0000-0000-000000000001/3.
[42951427.980000] uvcvideo: Adding mapping Exposure (Absolute) to control 00000000-0000-0000-0000-000000000001/4.
[42951427.980000] uvcvideo: Adding mapping White Balance Temperature, Auto to control 00000000-0000-0000-0000-000000000101/11.
[42951427.980000] uvcvideo: Adding mapping White Balance Temperature to control 00000000-0000-0000-0000-000000000101/10.
[42951427.980000] uvcvideo: Adding mapping White Balance Component, Auto to control 00000000-0000-0000-0000-000000000101/13.
[42951427.980000] uvcvideo: Adding mapping White Balance Blue Component to control 00000000-0000-0000-0000-000000000101/12.
[42951427.980000] uvcvideo: Adding mapping White Balance Red Component to control 00000000-0000-0000-0000-000000000101/12.
[42951427.980000] uvcvideo: Adding mapping Focus (absolute) to control 00000000-0000-0000-0000-000000000001/6.
[42951427.980000] uvcvideo: Adding mapping Focus, Auto to control 00000000-0000-0000-0000-000000000001/8.
[42951427.980000] usbcore: registered new driver uvcvideo
[42951427.980000] USB Video Class driver (SVN r205)

When i connect the cam I get (in dmesg):

[42951488.990000] usb 5-4: new high speed USB device using ehci_hcd and address 5
[42951489.170000] uvcvideo: Probing generic UVC device 4
[42951489.170000] uvcvideo: Found format YUV 4:2:2 (YUYV).
[42951489.170000] uvcvideo: - 640x480 (30.0 fps)
[42951489.170000] uvcvideo: - 352x288 (30.0 fps)
[42951489.170000] uvcvideo: - 320x240 (30.0 fps)
[42951489.170000] uvcvideo: - 176x144 (30.0 fps)
[42951489.170000] uvcvideo: - 160x120 (30.0 fps)
[42951489.170000] uvcvideo: - 1280x1024 (9.0 fps)
[42951489.170000] uvcvideo: Found format MJPEG.
[42951489.170000] uvcvideo: - 640x480 (30.0 fps)
[42951489.170000] uvcvideo: - 352x288 (30.0 fps)
[42951489.170000] uvcvideo: - 320x240 (30.0 fps)
[42951489.170000] uvcvideo: - 176x144 (30.0 fps)
[42951489.170000] uvcvideo: - 160x120 (30.0 fps)
[42951489.170000] uvcvideo: - 1280x1024 (15.0 fps)
[42951489.170000] uvcvideo: Found a Status endpoint (addr 83).
[42951489.170000] uvcvideo: Found UVC 1.00 device Philips SPC 1300NC Webcam (0471:0331)
[42951489.170000] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/2 to device 4 entity 3
[42951489.170000] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/3 to device 4 entity 3
[42951489.170000] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/6 to device 4 entity 3
[42951489.170000] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/7 to device 4 entity 3
[42951489.170000] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/8 to device 4 entity 3
[42951489.170000] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/9 to device 4 entity 3
[42951489.170000] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/1 to device 4 entity 3
[42951489.170000] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/4 to device 4 entity 3
[42951489.170000] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/5 to device 4 entity 3
[42951489.170000] uvcvideo: Added control 00000000-0000-0000-0000-000000000001/2 to device 4 entity 1
[42951489.170000] uvcvideo: Added control 00000000-0000-0000-0000-000000000001/3 to device 4 entity 1
[42951489.170000] uvcvideo: Added control 00000000-0000-0000-0000-000000000001/4 to device 4 entity 1
[42951489.170000] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/11 to device 4 entity 3
[42951489.170000] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/10 to device 4 entity 3
[42951489.170000] uvcvideo: Scanning UVC chain: OT 2 <- XU 5 <- XU 4 <- PU 3 <- IT 1
[42951489.170000] uvcvideo: Found a valid video chain (1 -> 2).
[42951489.180000] input: Philips SPC 1300NC Webcam as /class/input/input4
[42951489.180000] uvcvideo: UVC device initialized.
[42951489.210000] 5:3:1: cannot get freq at ep 0x84

Another webcam (Logitech) works perfectly with pwc module ...

Greetz

---

### Post by kriukov on 2009-01-21
The same problem. Has anyone managed to make a Philips webcam work?

---

### Post by walterav on 2009-06-30
Well it works in mint linux 7 gloria, which is ubuntu 9.04 based... it is only overexposed... so at night it is okay, but during a sunny day I don't see a thing...

---

