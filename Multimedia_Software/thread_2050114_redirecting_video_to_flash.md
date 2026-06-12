---
title: "redirecting video to flash"
date: 2012-08-30
forum: Multimedia Software
---

### Post by MikeCyber on 2012-08-30
Hi
I wonder how to play a *.avi for display in Firefox/flash? I've looked at:
[http://wdawe.com/index.php/finally-eeepc-camera-flash-suppport?blog=1](http://wdawe.com/index.php/finally-eeepc-camera-flash-suppport?blog=1)

but still couldn't figure if I could do that?
Thanks

---

### Post by AnotherMuggle on 2012-08-30
> **MikeCyber said:**
> Hi
I wonder how to play a *.avi for display in Firefox/flash? I've looked at:
[http://wdawe.com/index.php/finally-eeepc-camera-flash-suppport?blog=1](http://wdawe.com/index.php/finally-eeepc-camera-flash-suppport?blog=1)

but still couldn't figure if I could do that?
Thanks

If you download VLC player you can use the Convert feature to convert the .avi files to .webm, which will play in a recent version of FireFox.

---

### Post by MikeCyber on 2012-08-30
I want to use it for a flash chat site.

---

### Post by AnotherMuggle on 2012-08-30
> **MikeCyber said:**
> I want to use it for a flash chat site.

.webm is a HTML5 video format.

If you want flash videos then you can install FFMPEG and use a command similar to this:

```
ffmpeg -i inputvideo.avi outputvideo.flv
```

---

### Post by MikeCyber on 2012-08-30
does this work with /dev/video0 alike a webcam?

---

### Post by AnotherMuggle on 2012-08-30
> **MikeCyber said:**
> does this work with /dev/video0 alike a webcam?

I don't know from experience, I've never used a webcam in linux, but looking at FFMPEGs docs I'd say it's possible.

---

### Post by MikeCyber on 2012-08-31
ffmpeg  -an -f video4linux2 -s 640x480  -r 15 -i MVI*AVI  /dev/video0
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[video4linux2 @ 0xb339c0] ioctl(VIDIOC_QUERYCAP): Inappropriate ioctl for device
MVI_0294.AVI: Inappropriate ioctl for device

------
any help?

---

### Post by MikeCyber on 2012-09-14
Webcamstudio does the job and has even more features than ManyCam:
[http://code.google.com/p/webcamstudio/downloads/list](http://code.google.com/p/webcamstudio/downloads/list)

A bit slow and I needed to get used to, but yes works after changing Flash settings:
[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html)

---

