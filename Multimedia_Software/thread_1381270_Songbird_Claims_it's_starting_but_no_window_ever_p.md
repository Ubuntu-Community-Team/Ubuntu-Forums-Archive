---
title: "Songbird Claims it's starting but no window ever pops-up"
date: 2010-01-14
forum: Multimedia Software
---

### Post by Burky on 2010-01-14
I recently installed the newest version of Songbird, it worked for two days. Now when I click Songbird, it tells me it's starting down in the Window List, but it never pops up. 

I've tried all three methods from[ here]("https://help.ubuntu.com/community/Songbird") to install it afterwards... none of them I got to work.

Anyone have a clue what could possibly going on?

Oh and this is on Ubuntu 9.10(32bit)

---

### Post by Burky on 2010-01-19
I really dislike Rythmbox, and would prefer to use Songbird. Does anyone have an idea?

Possibly remove all the contents of Songbird that were ever on the my computer and try again?

---

### Post by Maheriano on 2010-01-19
Happened to me with Vuze. Start it from the terminal and post the output here, it's likely complaining about a missing dependency or Java.

---

### Post by Burky on 2010-01-19
No problem

```
david@david-desktop:~$ songbird

(songbird-bin:6254): GLib-WARNING **: g_set_prgname() called multiple times

(songbird-bin:6258): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstrawparse.so': /usr/lib/gstreamer-0.10/libgstrawparse.so: undefined symbol: gst_video_format_new_caps_interlaced

(songbird-bin:6258): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmpegdemux.so': /usr/lib/gstreamer-0.10/libgstmpegdemux.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:6258): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdeinterlace.so': /usr/lib/gstreamer-0.10/libgstdeinterlace.so: undefined symbol: gst_video_format_parse_caps_interlaced

(songbird-bin:6258): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstlibvisual.so': /usr/lib/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:6258): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type

(songbird-bin:6258): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgsthdvparse.so': /usr/lib/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:6258): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstavi.so': /usr/lib/gstreamer-0.10/libgstavi.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:6258): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmatroska.so': /usr/lib/gstreamer-0.10/libgstmatroska.so: undefined symbol: gst_util_array_binary_search

(songbird-bin:6258): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libresindvd.so': /usr/lib/gstreamer-0.10/libresindvd.so: undefined symbol: gst_navigation_event_parse_command

(songbird-bin:6258): GStreamer-WARNING **: invalid name template bwf_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:6258): GStreamer-WARNING **: invalid name template alaw_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:6258): GStreamer-WARNING **: invalid name template dv_dif_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:6258): GStreamer-WARNING **: invalid name template jpeg2000_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:6258): GStreamer-WARNING **: invalid name template mpeg_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:6258): GStreamer-WARNING **: invalid name template mpeg_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:6258): GStreamer-WARNING **: invalid name template up_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:6258): GStreamer-WARNING **: invalid name template vc3_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:6258): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstschro.so': /usr/lib/gstreamer-0.10/libgstschro.so: undefined symbol: gst_adapter_masked_scan_uint32

(songbird-bin:6258): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdv.so': /usr/lib/gstreamer-0.10/libgstdv.so: undefined symbol: gst_tag_list_new_full
././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

```

---

### Post by Burky on 2010-01-19
```
sudo mv /usr/lib/python2.6/dist-packages/gst-0.10/ /usr/lib/python2.6/dist-packages/gst-0.10_bad

```

That code did the trick for Sonbird, however will this effect other applications?

---

### Post by Maheriano on 2010-01-19
> **Burky said:**
> ```
sudo mv /usr/lib/python2.6/dist-packages/gst-0.10/ /usr/lib/python2.6/dist-packages/gst-0.10_bad

```

That code did the trick for Sonbird, however will this effect other applications?

You mean affect? To be honest I don't even know why that would work for Songbird, are you saying it's working now?

---

### Post by Burky on 2010-01-19
> **Maheriano said:**
> You mean affect? To be honest I don't even know why that would work for Songbird, are you saying it's working now?

Yes.

---

