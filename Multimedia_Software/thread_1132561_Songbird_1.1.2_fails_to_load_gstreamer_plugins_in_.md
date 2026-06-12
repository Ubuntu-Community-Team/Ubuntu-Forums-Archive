---
title: "Songbird 1.1.2 fails to load gstreamer plugins in Jaunty"
date: 2009-04-22
forum: Multimedia Software
---

### Post by athleticbum32 on 2009-04-22
I have had a few issues regarding songbird recognizing and playing wma files from my music collection. When importing my library mp3 files are recognized and play fine, but wma files contain missing tag information and album art. In Intrepid wma files would still play, but after my upgrade to Jaunty I get an media core error when a wma file is selected to play. I have loaded all gstreamer-plugins-0.10 in the repos and have verified that wma files will display tag info and play correctly in rhythmbox and movie player.

nick@UpInFlames:~$ songbird

(songbird-bin:8080): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstreal.so': /usr/lib/gstreamer-0.10/libgstreal.so: undefined symbol: gst_plugin_add_dependency_simple

(songbird-bin:8080): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstgio.so': /usr/lib/gstreamer-0.10/libgstgio.so: undefined symbol: gst_query_set_uri

(songbird-bin:8080): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstcelt.so': /usr/lib/gstreamer-0.10/libgstcelt.so: undefined symbol: gst_tag_setter_reset_tags

(songbird-bin:8080): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': /usr/lib/gstreamer-0.10/libgstffmpeg.so: undefined symbol: gst_tag_setter_reset_tags

(songbird-bin:8080): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmetadata.so': /usr/lib/gstreamer-0.10/libgstmetadata.so: undefined symbol: gst_tag_setter_reset_tags

(songbird-bin:8080): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmxf.so': /usr/lib/gstreamer-0.10/libgstmxf.so: undefined symbol: gst_byte_reader_skip

(songbird-bin:8080): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstlibvisual.so': /usr/lib/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_plugin_add_dependency_simple

(songbird-bin:8080): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstladspa.so': /usr/lib/gstreamer-0.10/libgstladspa.so: undefined symbol: gst_plugin_add_dependency_simple

(songbird-bin:8080): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstflv.so': /usr/lib/gstreamer-0.10/libgstflv.so: undefined symbol: gst_byte_reader_skip

(songbird-bin:8080): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstqtmux.so': /usr/lib/gstreamer-0.10/libgstqtmux.so: undefined symbol: gst_tag_setter_reset_tags

(songbird-bin:8080): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstgnomevfs.so': /usr/lib/gstreamer-0.10/libgstgnomevfs.so: undefined symbol: gst_query_set_uri

Thanks, I appreciate any help.

---

### Post by athleticbum32 on 2009-04-22
I just downloaded the latest nightly build Songbird_1.2.0a-1060 and it started up error free. The wma files play fine, but they still are missing tag info (ex. track #, time) and album art. If this is my biggest problem, I think I can live with that.

---

