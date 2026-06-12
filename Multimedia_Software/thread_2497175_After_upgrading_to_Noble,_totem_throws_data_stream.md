---
title: "After upgrading to Noble, totem throws data stream error when going fullscreen"
date: 2024-04-25
forum: Multimedia Software
---

### Post by Wise Ferret on 2024-04-25
After upgrading from Mantic to Noble, totem throws "data stream error" message when going fullscreen while playing mkv files and stops playing. 
vlc works fine. I use the latest nvidia proprietary driver (550).

This is what I get in the terminal with debug level of 2:

```
totem --gst-debug-level=2 ~/myfolder/myfile.mkv 
0:00:00.470572340 68919 0x7a92780014d0 WARN           matroskademux matroska-demux.c:1465:gst_matroska_demux_parse_stream: Unknown TrackEntry subelement 0x22b59d - ignoring
0:00:00.481799136 68919 0x7a92780014d0 WARN               cudanvrtc gstcudanvrtc.cpp:152:gst_cuda_nvrtc_load_library_once: Could not open nvrtc library libnvrtc.so: cannot open shared object file: No such file or directory
0:00:01.648461580 68919 0x7a92780014d0 WARN           matroskademux matroska-demux.c:1465:gst_matroska_demux_parse_stream: Unknown TrackEntry subelement 0x22b59d - ignoring
0:00:01.649514280 68919 0x7a92780014d0 WARN           matroskademux matroska-demux.c:1465:gst_matroska_demux_parse_stream: Unknown TrackEntry subelement 0x22b59d - ignoring

[... many more almost identical warnings]

0:00:01.741126845 68919 0x6181c4a53400 WARN                   totem bacon-video-widget.c:1563:bvw_update_tags: Pipeline sent audio tags update with no changes
0:00:01.745140254 68919 0x6181c4a53400 WARN                   totem bacon-video-widget.c:1563:bvw_update_tags: Pipeline sent video tags update with no changes
0:00:01.871843062 68919 0x6181c4a53400 WARN               structure gststructure.c:2099:priv_gst_structure_append_to_gstring: No value transform to serialize field 'event' of type 'GstEvent'
0:00:01.871856388 68919 0x6181c4a53400 WARN                   totem bacon-video-widget.c:1276:bvw_handle_element_message: Unhandled element message GstNavigationMessage from sink: element message: 0x6181c63e8260, time 99:99:99.999999999, seq-num 9108, element 'sink', GstNavigationMessage, type=(string)event, event=(GstEvent)NULL;
0:00:01.939568859 68919 0x6181c4a53400 WARN               structure gststructure.c:2099:priv_gst_structure_append_to_gstring: No value transform to serialize field 'event' of type 'GstEvent'
0:00:01.939616113 68919 0x6181c4a53400 WARN                   totem bacon-video-widget.c:1276:bvw_handle_element_message: Unhandled element message GstNavigationMessage from sink: element message: 0x6181c57c7590, time 99:99:99.999999999, seq-num 10496, element 'sink', GstNavigationMessage, type=(string)event, event=(GstEvent)NULL;

[... many more almost identical warnings]

0:00:02.935629537 68919 0x7a9278008790 WARN                GST_CAPS gstpad.c:3266:gst_pad_query_accept_caps_default:<renderer:video_sink> caps: video/x-raw(memory:GLMemory), format=(string)NV12, width=(int)1920, height=(int)1080, interlace-mode=(string)progressive, multiview-mode=(string)mono, multiview-flags=(GstVideoMultiviewFlagsSet)0:ffffffff:/right-view-first/left-flipped/left-flopped/right-flipped/right-flopped/half-aspect/mixed-mono, pixel-aspect-ratio=(fraction)1/1, colorimetry=(string)bt709, framerate=(fraction)24/1, texture-target=(string)2D were not compatible with: EMPTY
0:00:02.935698349 68919 0x7a9278008790 WARN           basetransform gstbasetransform.c:1371:gst_base_transform_setcaps:<pre-colorspace> transform could not transform video/x-raw(memory:GLMemory), format=(string)NV12, width=(int)1920, height=(int)1080, interlace-mode=(string)progressive, multiview-mode=(string)mono, multiview-flags=(GstVideoMultiviewFlagsSet)0:ffffffff:/right-view-first/left-flipped/left-flopped/right-flipped/right-flopped/half-aspect/mixed-mono, pixel-aspect-ratio=(fraction)1/1, colorimetry=(string)bt709, framerate=(fraction)24/1, texture-target=(string)2D in anything we support
0:00:02.935735606 68919 0x7a9278008790 WARN           basetransform gstbasetransform.c:1432:gst_base_transform_reconfigure_unlocked:<pre-colorspace> warning: not negotiated
0:00:02.935752773 68919 0x7a9278008790 WARN           basetransform gstbasetransform.c:1432:gst_base_transform_reconfigure_unlocked:<pre-colorspace> warning: not negotiated
0:00:02.973542789 68919 0x6181c4a53400 WARN               structure gststructure.c:2099:priv_gst_structure_append_to_gstring: No value transform to serialize field 'gerror' of type 'GError'
0:00:02.973578827 68919 0x6181c4a53400 WARN                   totem bacon-video-widget.c:1881:bvw_bus_message_cb: Warning message: warning message: 0x7a90d401d3d0, time 99:99:99.999999999, seq-num 15753, element 'pre-colorspace', GstMessageWarning, gerror=(GError)NULL, debug=(string)"../libs/gst/base/gstbasetransform.c\(1432\):\ gst_base_transform_reconfigure_unlocked\ \(\):\ /GstPlayBin:play/GstPlaySink:playsink/GstBin:tbin/GstSubtitleOverlay:suboverlay/GstVideoConvert:pre-colorspace:\012not\ negotiated";
0:00:03.007994622 68919 0x7a92780014d0 WARN           matroskademux matroska-demux.c:6115:gst_matroska_demux_loop:<matroskademux0> error: Internal data stream error.
0:00:03.008007142 68919 0x7a92780014d0 WARN           matroskademux matroska-demux.c:6115:gst_matroska_demux_loop:<matroskademux0> error: streaming stopped, reason not-negotiated (-4)
0:00:03.008121349 68919 0x6181c4a53400 ERROR                default totem-gst-helpers.c:61:totem_gst_message_print: message = Internal data stream error.
0:00:03.008133325 68919 0x6181c4a53400 ERROR                default totem-gst-helpers.c:62:totem_gst_message_print: domain  = 7840 (gst-stream-error-quark)
0:00:03.008137769 68919 0x6181c4a53400 ERROR                default totem-gst-helpers.c:64:totem_gst_message_print: code    = 1
0:00:03.008144195 68919 0x6181c4a53400 ERROR                default totem-gst-helpers.c:65:totem_gst_message_print: debug   = ../gst/matroska/matroska-demux.c(6115): gst_matroska_demux_loop (): /GstPlayBin:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin:decodebin0/GstMatroskaDemux:matroskademux0:
streaming stopped, reason not-negotiated (-4)
0:00:03.008183030 68919 0x6181c4a53400 ERROR                default totem-gst-helpers.c:66:totem_gst_message_print: source  = <matroskademux0>
0:00:03.008188706 68919 0x6181c4a53400 ERROR                default totem-gst-helpers.c:67:totem_gst_message_print: uri     = (NULL)
```

In Mantic same file played well. ubuntu-restricted-extras is installed, gstreamer-vaapi is installed. Any ideas about what is going on?

---

### Post by #&amp;thj^% on 2024-04-25
Sounds like a bug against totem, and Noble of course is still very wet behind the ears. (But you knew that)

---

