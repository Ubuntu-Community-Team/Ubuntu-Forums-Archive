---
title: "Is Sandy Bridge hardware encoding supported?"
date: 2011-08-28
forum: Multimedia Software
---

### Post by tokyo-joe on 2011-08-28
I heard hardware mp4 movie encoding is supported on Windows with Intel Sandy Bridge CPUs and it's insanely fast.

Is h/w mp4 encoding supported on Ubuntu, too?

I use Maverick for your reference.

---

### Post by BicyclerBoy on 2011-08-29
[http://intellinuxgraphics.org/h264.html](http://intellinuxgraphics.org/h264.html)

Look like yes..but is there any application to drive it ?
You would have to check the ffmpeg/gstreamer forums.
I imagine VA-API is used.
Looks like you need kernel 3.

I have seen reports that intel quicksync video quality was not as good x264.

---

### Post by freechelmi on 2012-10-29
Hi, I had the same question and was glad to see that a dev at intel has produced code that could encode H264 using gstreamer for SandyBridge

[http://gitorious.org/vaapi/gstreamer-vaapi/merge_requests/5](http://gitorious.org/vaapi/gstreamer-vaapi/merge_requests/5)

That would be excellent for Arista !

---

