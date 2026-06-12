---
title: "Creative Webcam not working"
date: 2009-05-16
forum: Multimedia Software
---

### Post by motters on 2009-05-16
I've been using Creative Webcam NX Ultra cameras for the last few years very successfully with previous versions of Ubuntu.  However, in Jaunty they now no longer seem to work.

I think these cameras use the spca driver which I think in
most cases is part of the kernel.  It might be in this case that
something has changed relating to the spca kernel driver.  I also have
a more modern UVC compliant camera built into the laptop, and that
seems to work ok, so it looks as if the problem only applies to
certain older webcams.

As a piece of superfluous information, the Webcams are part of a dual stereo vision head on a mobile robot.

lsmod shows:

```
gspca_main             29952  1 gspca_spca505
compat_ioctl32          9344  1 uvcvideo
videodev               41600  2 uvcvideo,gspca_main
v4l1_compat            21764  2 uvcvideo,videodev

```

lsusb shows:

```
Bus 002 Device 009: ID 0403:6001 Future Technology Devices
International, Ltd FT232 USB-Serial (UART) IC
Bus 002 Device 008: ID 06c2:0045 Phidgets Inc. (formerly GLAB)
PhidgetInterface Kit 8-8-8
Bus 002 Device 012: ID 06c2:0059 Phidgets Inc. (formerly GLAB)
Bus 002 Device 013: ID 06c2:0080 Phidgets Inc. (formerly GLAB)
Bus 002 Device 011: ID 06c2:0080 Phidgets Inc. (formerly GLAB)
Bus 002 Device 010: ID 06c2:0038 Phidgets Inc. (formerly GLAB) 4-Motor
PhidgetServo v3.0
Bus 002 Device 007: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 006: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 041e:401d Creative Technology, Ltd WebCam NX
Ultra
Bus 006 Device 002: ID 041e:401d Creative Technology, Ltd WebCam NX
Ultra
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 041e:401d Creative Technology, Ltd WebCam NX
Ultra
Bus 005 Device 002: ID 041e:401d Creative Technology, Ltd WebCam NX
Ultra
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd
<-- the UVC camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

and video devices:

```
/dev/video0  /dev/video1  /dev/video2  /dev/video3  /dev/video4

```

running fswebcam (a utility which I've been using successfully for a long while):

```
fswebcam -d /dev/video1
--- Opening /dev/video1...
Trying source module v4l2...
/dev/video1 opened.
No input was specified, using the first.
Unable to find a compatible palette format.

```

and also using LD_PRELOAD...

```
LD_PRELOAD=/usr//lib/libv4l/v4l1compat.so fswebcam -d /dev/video1
--- Opening /dev/video1...
Trying source module v4l2...
/dev/video1 opened.
No input was specified, using the first.
Adjusting resolution from 384x288 to 352x288.
--- Capturing frame...
Timed out waiting for frame!
Segmentation fault
```

---

