---
title: "Webcam motion detection with GStreamer"
date: 2009-01-05
forum: Multimedia Software
---

### Post by marmuta on 2009-01-05
Hi, has anybody heard of a motion detection plugin for gstreamer?
I know of "motion" but that's a bit inflexible and doesn't work so well with my camera, whereas gstreamer does.

I'm thinking of a kind of filter that would let frames through only if there was motion detected, e.g. like this:

gst-launch-0.10 v4l2src ! ffmpegcolorspace ! **motiondetect** ! ... ! filesink location=motion.mjpeg

---

### Post by marmuta on 2009-01-06
*bump*

anyone?

---

### Post by hackeron on 2011-06-30
This looks very interesting: [https://gitorious.org/gstreamer-motion-plugin](https://gitorious.org/gstreamer-motion-plugin)

---

### Post by hackeron on 2011-07-01
Also have a read through this discussion: [https://bugzilla.gnome.org/show_bug.cgi?id=629244](https://bugzilla.gnome.org/show_bug.cgi?id=629244)

---

