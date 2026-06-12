---
title: "ffmpeg makes empty files from EasyCAP"
date: 2019-10-02
forum: Multimedia Software
---

### Post by wlraider70 on 2019-10-02
HI,

I'm trying to use a headless ubuntu server to mess with a video feed into the machine, but before I can do anything fancy I just want to record a file off the input.
I have tried a dozen variations of 'sudo ffmpeg -f video4linux2 -s 432*240 -r 5 -pixel_format yuyv422 -i /dev/video0 out3.mkv -loglevel debug' with different -f options or -s options.

Regardless of what small changes I make to frame rate or size, I get **Finishing stream 0:0 without any data written to it.**
I'm wondering if it has anything to do with the fact that I don't have X or gnome or whatever the desktop version uses right now. 


```
$ lsusb
Bus 001 Device 002: ID 1b71:3002 Fushicai USBTV007 Video Grabber [EasyCAP]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 0658:0200 Sigma Designs, Inc. 
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ sudo v4l2-ctl -d /dev/video0 --info
Driver Info (not using libv4l2):
	Driver name   : usbtv
	Card type     : usbtv
	Bus info      : usb-0000:02:01.0-1
	Driver version: 4.15.18
	Capabilities  : 0x85200001
		Video Capture
		Read/Write
		Streaming
		Extended Pix Format
		Device Capabilities
	Device Caps   : 0x05200001
		Video Capture
		Read/Write
		Streaming
		Extended Pix Format
```

thanks

---

