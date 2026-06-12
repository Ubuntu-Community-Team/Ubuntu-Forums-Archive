---
title: "Symbol Lookup Error in Songbird"
date: 2010-03-03
forum: Multimedia Software
---

### Post by Maxcore on 2010-03-03
Hello ladies and gentlemen. Whenever I try to run Songbird it no longer opens. I used it last night before turning off my computer and now that I have turned it back on it no longer works. Launching it through the launches yields nothing and launching it through the shell gives me this output:

```
$ ./songbird

(songbird-bin:3824): GLib-WARNING **: g_set_prgname() called multiple times

(songbird-bin:3828): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstrawparse.so': /usr/lib64/gstreamer-0.10/libgstrawparse.so: undefined symbol: gst_video_format_new_caps_interlaced

(songbird-bin:3828): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstlibvisual.so': /usr/lib64/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:3828): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstdeinterlace.so': /usr/lib64/gstreamer-0.10/libgstdeinterlace.so: undefined symbol: gst_video_format_parse_caps_interlaced

(songbird-bin:3828): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstmpegdemux.so': /usr/lib64/gstreamer-0.10/libgstmpegdemux.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:3828): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type

(songbird-bin:3828): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstmatroska.so': /usr/lib64/gstreamer-0.10/libgstmatroska.so: undefined symbol: gst_util_array_binary_search

(songbird-bin:3828): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgsthdvparse.so': /usr/lib64/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:3828): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstdv.so': /usr/lib64/gstreamer-0.10/libgstdv.so: undefined symbol: gst_tag_list_new_full

(songbird-bin:3828): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstschro.so': /usr/lib64/gstreamer-0.10/libgstschro.so: undefined symbol: gst_adapter_masked_scan_uint32

(songbird-bin:3828): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstavi.so': /usr/lib64/gstreamer-0.10/libgstavi.so: undefined symbol: _gst_debug_dump_mem
././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

```

I am not quite sure what the problem is. Does anyone know a solution to this problem? I am running 9.10.

---

### Post by subwayne on 2010-03-04
It is an incompatibility with GStreamer. Just remove all files beginning with libgst* in the songbird/lib folder. For me, Songbird is running after removing the files. It is still a workaround.

---

### Post by Maxcore on 2010-03-04
Do you have any idea what causes this problem? I have been using the program for months, it seems weird that it would just stop working.

---

### Post by go_beep_yourself on 2010-03-18
> **subwayne said:**
> It is an incompatibility with GStreamer. Just remove all files beginning with libgst* in the songbird/lib folder. For me, Songbird is running after removing the files. It is still a workaround.

Worked for me :popcorn:

Do podcast work good in Songbird?

---

