---
title: "Can't get ffmpeg to work"
date: 2007-01-14
forum: Multimedia &amp; Video
---

### Post by silhouette on 2007-01-14
I've been trying to get ffmpeg to work so I can record video from my webcam. Every time I run it (using something like `ffmpeg -vd /dev/video -ad /dev/dsp -r 10 -s 352x288 video.avi`) I get this error:

ioctl(VIDIOC_QUERYCAP): Invalid argument
Could not find video grab device

I've tried all sorts of argument combinations, and I'm SURE that I'm entering the right thing. I've been all over the web trying to search for a solution.... does anyone have any sort of idea why this error would pop up?

---

### Post by david_2001 on 2007-01-14
The error message is telling you that there is no recognisable video device attached to /dev/video.  You're probably best advised to work your way through the HOWTO [[COLOR="RoyalBlue"]_here_[/COLOR]]("http://www.linux.com/howtos/Webcam-HOWTO/index.shtml") and then ask again.

---

### Post by silhouette on 2007-01-15
Well, I've got the driver installed -- it's a Logitech Quickcam Chat and I found out it uses the gspca (aka spca5xx) driver. And camorama, gqcam, streamer (suggested by that howto you gave), and ekiga all work fine, but ffmpeg just doesn't want to. xawtv doesn't work either, though that may be a different problem, I'm not sure.

---

### Post by ipavkovic on 2007-02-28
Hi there,

perhaps you should try different screen sizes and or frame rates (just play around with -s 320x240,  -s 640x480).

For me the following worked:

"ffmpeg -vd /dev/video -ad /dev/dsp -s 352x288 out.mgp"

I have a Philips webcam (lsusb tells me "0471:0327 Philips") and use the driver gspca.

Best Regards,
[INDENT]Ilja Pavkovic[/INDENT]

---

### Post by LAcike on 2007-04-27
No. It is not because of wrong settings. Your camera driver is probably using only v4l (version 1) and your version of ffmpeg uses v4l2 (version 2). Try older release of ffmpeg or get the newest one, it should use v4l again.

see:
[http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-April/002808.html](http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-April/002808.html)

You'll also expect the same problem when using mpeg4ip :(
The error is during initialization - quering the device, what it is capable of. Unfortunately, v4l and v4l2 have different query syntax.

---

