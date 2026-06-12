---
title: "Songbird gives GStreamer Error after upgrade"
date: 2009-11-01
forum: Multimedia Software
---

### Post by nexist on 2009-11-01
I upgraded to 9.10 last night. In the morning, I decided to listen to some music. Songbird wouldn't start. I went to a terminal and ran it there:

```
(songbird-bin:2571): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstdeinterlace.so': /usr/lib64/gstreamer-.10/libgstdeinterlace.so: undefined symbol: gst_video_format_parse_caps_interlaced
././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type 
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal
```

I am running 1.2 which seems to be the latest version. This all worked yesterday as I was playing spooky music to scare the trick-or-treaters.

---

