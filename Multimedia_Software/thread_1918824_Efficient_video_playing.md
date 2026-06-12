---
title: "Efficient video playing"
date: 2012-02-01
forum: Multimedia Software
---

### Post by Hetepeperfan on 2012-02-01
Hello all,

I'm beginning to get a little bit acquainted with gstreamer. Now I'm wondering if I'm developing an application what kind of video streams do graphics hardware and the xwindow system like. I have a camera that can provide me with YUV and raw 8bit unsigned data streams via an API. Now I'm wondering how to get this stream efficiently to the screen.
So whats best performance wise the best way to get this to the screen.

now I have a pipeline that is GstAppSource | capsfilter ("video/raw-gray") | ffmpegcolorspace | xvimagesink.

Is there a more efficient way to do this?

Kind regards

---

