---
title: "Totem, codecs, permissions and sudo."
date: 2010-05-09
forum: Multimedia Software
---

### Post by wbrb on 2010-05-09
I'm on my 5th install of Lucid Desktop.

I enabled medibuntu, installed ubuntu-restricted-extras and totem still won't play most video formats. So I removed them --purge'd them and tried again. Still nothing.

I read a bunch of articles and everything looked like it was installed but a post recommended installing libtotem-plpparser which I did which caused one or two formats to work. 

For some reason I tried totem with gksudo and I can say totem now works perfectly with gksudo and without it it complains that it needs to search for codecs and finds none.

I'm not familiar enough with the codec handling mechanisms to figure out what permissions or files need to be modified to correct this.

Anybody want to take a crack at it?

---

### Post by tekkidd on 2010-05-09
open up the ubuntu software center and search for gstr. the search restults will come up with a whole bunch of gstreemer plug ins. install all of them. thats just about all to it.

---

### Post by wbrb on 2010-05-09
sudo apt-get install gstreamer0.10-plugins* installed 30 Megs. Still nothing on WMV AVI or FLV. MPEG is still working nicely.

---

### Post by wbrb on 2010-05-09
opening various types of media without sudo, the terminal shows:
> 
wbrb@compy:/usr/share/gstreamer-0.10/presets$ totem
** Message: Missing plugin: gstreamer|0.10|totem|On2 VP6/Flash decoder|decoder-video/x-vp6-flash (On2 VP6/Flash decoder)
** Message: No installation candidate for missing plugins found.

(totem:4149): GStreamer-CRITICAL **: gst_query_set_duration: assertion `GST_QUERY_TYPE (query) == GST_QUERY_DURATION' failed

(totem:4149): GStreamer-CRITICAL **: gst_query_set_duration: assertion `GST_QUERY_TYPE (query) == GST_QUERY_DURATION' failed

(totem:4149): GStreamer-CRITICAL **: gst_query_set_duration: assertion `GST_QUERY_TYPE (query) == GST_QUERY_DURATION' failed
** Message: Error: The stream is encrypted and decryption is not supported.
gstasfdemux.c(3673): gst_asf_demux_process_object (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstASFDemux:asfdemux0

** Message: Missing plugin: gstreamer|0.10|totem|DivX MPEG-4 Version 5 decoder|decoder-video/x-divx, divxversion=(int)5 (DivX MPEG-4 Version 5 decoder)


with gksudo it shows:
> 
wbrb@compy:/usr/share/gstreamer-0.10/presets$ gksudo totem
(totem:4197): Totem-WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Total Unfree 60 bytes cnt 1 [(nil),0]
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Total Unfree 120 bytes cnt 2 [(nil),0]


---

### Post by wbrb on 2010-05-09
I fixed it.

Apparently somehow rhythm box was uninstalled. I assume it was me messing around with getting the codecs running. I realised when i tried to play Mp3's in rhythm box it wasn't there. It would seem that the reinstallation of rhythm box corrected the use of codecs in totem / move player.

If anybody has an explanation I would love to hear it, but either way  it's working again. Not sure how to mark this solved.

---

