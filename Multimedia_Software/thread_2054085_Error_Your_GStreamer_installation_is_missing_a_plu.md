---
title: "Error: Your GStreamer installation is missing a plug-in."
date: 2012-09-06
forum: Multimedia Software
---

### Post by grooverider on 2012-09-06
Hi guys,

I have done a fresh install of ubuntu 12.04 64 bit version, also have a dvb-s card with tvheadend, all works fine, however when I want to watch in firefox i get the following error messages, tried to fix it with multiple things not working, what do I need to do???:

funky1@SAT:~$ firefox
argv[0] class  x-panel
argv[1] id DCRgQXvT
argv[2] autoplay no
argv[3] version VideoLAN.VLCPlugin.2
argv[4] pluginspage [http://www.videolan.org](http://www.videolan.org)
argv[5] type application/x-vlc-plugin
argv[6] height 100%
argv[7] width 100%
 
** (plugin-container:5580): WARNING **: WARNING: function totemConePlaylist::playItem is unimplemented
Viewer: SetWindow XID 56660387 size 507:384
Referrer URI: [http://localhost:9981/extjs.html](http://localhost:9981/extjs.html)
TotemEmbedded-Message: Viewer state: STOPPED
TotemEmbedded-Message: totem_embedded_clear_playlist
Emptying current_uri
TotemEmbedded-Message: totem_embedded_add_item: playlist/channelid/202 (base: [http://localhost:9981/extjs.html](http://localhost:9981/extjs.html) title:  subtitle: )
totem_embedded_set_uri uri playlist/channelid/202 base [http://localhost:9981/extjs.html](http://localhost:9981/extjs.html) => resolved [http://localhost:9981/playlist/channelid/202](http://localhost:9981/playlist/channelid/202) (subtitle  => resolved [http://localhost:9981/](http://localhost:9981/))
TotemEmbedded-Message: totem_embedded_open_internal 'http://localhost:9981/playlist/channelid/202' subtitle 'http://localhost:9981/' is-browser-stream 0 start-play 0
TotemEmbedded-Message: Mimetype 'application/x-vlc-plugin' doesn't have a handler
** Message: Error: Your GStreamer installation is missing a plug-in.
gstdecodebin2.c(3576): gst_decode_bin_expose (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin21:
no suitable plugins found
 
** Message: Missing plugin: gstreamer|0.10|totem-plugin-viewer|text/uri-list decoder|decoder-text/uri-list (text/uri-list decoder)
** Message: Missing plugin: gstreamer|0.10|totem-plugin-viewer|text/html decoder|decoder-text/html (text/html decoder)
/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject

---

