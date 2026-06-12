---
title: "Webcam C920 Issues"
date: 2014-02-16
forum: Multimedia Software
---

### Post by byt0x on 2014-02-16
Hi,

i bought a Logitech C920 for imageprocessing via OpenCV:
Problem now is that i cannot watch videos with a resolution
of 1920x1080px! Just with 640x480. Thats nothing!

In this video it looks like there is no problem in Ubuntu with this
camera [http://www.youtube.com/watch?v=8QouvYMfmQo](http://www.youtube.com/watch?v=8QouvYMfmQo)
but the Output of v4l2-ctl is different from mine.

Here a screenshot with the output from the video:
[ATTACH=CONFIG]250407[/ATTACH][ATTACH=CONFIG]250408[/ATTACH]

v4l2-ctl --all
```
Driver Info (not using libv4l2):
	Driver name   : uvcvideo
	Card type     : BisonCam, NB Pro
	Bus info      : usb-0000:00:1a.7-1
	Driver version: 3.8.8
	Capabilities  : 0x84000001
		Video Capture
		Streaming
		Device Capabilities
	Device Caps   : 0x04000001
		Video Capture
		Streaming
Priority: 2
Video input : 0 (Camera 1: ok)
Format Video Capture:
	Width/Height  : 1280/1024
	Pixel Format  : 'YUYV'
	Field         : None
	Bytes per Line: 2560
	Size Image    : 2621440
	Colorspace    : Unknown (00000000)
Crop Capability Video Capture:
	Bounds      : Left 0, Top 0, Width 1280, Height 1024
	Default     : Left 0, Top 0, Width 1280, Height 1024
	Pixel Aspect: 1/1
Streaming Parameters Video Capture:
	Capabilities     : timeperframe
	Frames per second: 7.000 (7/1)
	Read buffers     : 0
                     brightness (int)    : min=0 max=100 step=1 default=50 value=50
                       contrast (int)    : min=0 max=6 step=1 default=3 value=3
                     saturation (int)    : min=0 max=8 step=1 default=4 value=4
                            hue (int)    : min=-4 max=4 step=1 default=0 value=0
                          gamma (int)    : min=0 max=7 step=1 default=5 value=5
           power_line_frequency (menu)   : min=0 max=2 default=2 value=2
                      sharpness (int)    : min=0 max=100 step=1 default=65 value=65
         backlight_compensation (int)    : min=0 max=4 step=1 default=0 value=4

```

v4l2-ctl --list-formats
```
ioctl: VIDIOC_ENUM_FMT
	Index       : 0
	Type        : Video Capture
	Pixel Format: 'MJPG' (compressed)
	Name        : MJPEG

	Index       : 1
	Type        : Video Capture
	Pixel Format: 'YUYV'
	Name        : YUV 4:2:2 (YUYV)


```

uname -a
```
Linux marcel-laptop 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

dmesg
```
[ 2641.476096] usb 2-2: new high-speed USB device number 5 using ehci-pci
[ 2641.610445] usb 2-2: New USB device found, idVendor=046d, idProduct=082d
[ 2641.610449] usb 2-2: New USB device strings: Mfr=0, Product=2, SerialNumber=1
[ 2641.610452] usb 2-2: Product: HD Pro Webcam C920
[ 2641.610454] usb 2-2: SerialNumber: E48AAE8F
[ 2641.611114] uvcvideo: Found UVC 1.00 device HD Pro Webcam C920 (046d:082d)
[ 2641.611792] input: HD Pro Webcam C920 as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/input/input13

```

Why it does not work? I cannot understand why and why the output of v4l2 is different then the output in this video.
Please help. I need that camera for my work.

Note: I'am using Linux Mint!

Regards
Marcel

---

