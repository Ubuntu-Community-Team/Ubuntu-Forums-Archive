---
title: "Songbird Error"
date: 2010-01-06
forum: Multimedia Software
---

### Post by caglar.dursun on 2010-01-06
Hi 

It has to be a solution for this problem.I have Ubuntu 9.10 and I install Songbird 1.4 from binary package but I get an error.

(songbird-bin:21405): GLib-WARNING **: g_set_prgname() called multiple times

(songbird-bin:21409): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstavi.so': /usr/lib/gstreamer-0.10/libgstavi.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:21409): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type
ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml
././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type


I know there is no problem at my gstreamer.I mean , If the problem was gstreamer then totem player doesn't work to.So what can I do about it ?

---

