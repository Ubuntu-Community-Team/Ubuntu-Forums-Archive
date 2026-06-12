---
title: "Unable to play videos in Totem after installing Openshot"
date: 2009-11-28
forum: Multimedia Software
---

### Post by OrangeVixen on 2009-11-28
After installing Openshot, Toten won't play any video. When I try to open a video in Totem it says:


An error occurred

GStreamer encountered a general stream error.


From the command line it says:

```

** Message: Error: GStreamer encountered a general stream error.
qtdemux.c(2041): gst_qtdemux_loop (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstQTDemux:qtdemux0:
streaming stopped, reason not-negotiated

```

I already tried reinstalling totem and gstreamer.

Any ideas?

---

### Post by mc4man on 2009-11-29
see[ here]("http://ubuntuforums.org/showthread.php?t=1281367"), various ways to do the same thing

If you wish openshot there is a .deb install avail. that won't upgrade your ffmpeg libs and break your players

edit
here is the 'good' openshot ppa/deb
[https://launchpad.net/~jonoomph/+archive/openshot-edge](https://launchpad.net/~jonoomph/+archive/openshot-edge)

---

