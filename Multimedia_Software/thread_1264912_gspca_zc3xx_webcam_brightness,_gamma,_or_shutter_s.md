---
title: "gspca_zc3xx webcam brightness, gamma, or shutter speed?"
date: 2009-09-12
forum: Multimedia Software
---

### Post by skcoyote on 2009-09-12
Hi all,

I have a USB webcam plugged in to a Ubuntu 9.04 server (headless, no X). The webcam shows up as the following in lsusb:

```
Bus 002 Device 003: ID 046d:08ad Logitech, Inc. QuickCam Communicate STX
```

Additionally it comes up as /dev/video0 via the gspca_zc3xx driver. If I cat /dev/video0 > out.jpg, I get JPEG frames. So I run ffmpeg as follows:

```
ffmpeg -f mjpeg -s 320x240 -i /dev/video0 out.mpg
```

This works beautifully... *except,* the deal breaker is, there seems to be no adaptive brightness control, so if I point it outside in the daylight, the frame is completely white. Inside with the lights off, the brightness is adequate. This doesn't seem to change if I abruptly move the camera from light/dark (or vice versa) very quickly.

Is there a way to enable adaptive brightness control with the gspca driver or ffmpeg itself? Or, is there a way to statically set a brightness, gamma, or even shutter speed value for the camera? modinfo doesn't suggest any useful params, unfortunately.

Please remember that **I'm doing this on a headless server with no X**, so graphical interfaces are out. Assuming I can get reasonable daylight lighting, this camera will be part of a simple video surveillance system.

---

