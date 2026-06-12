---
title: "can't run rhythmbox totem"
date: 2011-07-28
forum: Multimedia Software
---

### Post by shbk on 2011-07-28
when i'm trying to run rhythmbox i receive:



(rhythmbox:7949): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed rhythmbox: symbol lookup error: /usr/lib/python2.7/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_date_time_get_type
  

i 've tried to do this:
  may be problem is in gstreamer, 

i write  apt-get install gstreamer and receive:
  gstreamer0.10-alsa is already the newest version. 

gstreamer0.10-esd is already the newest version.
 l
ong list of operations that shows that i have newest version of gstreamer
  

after i'd thought that problem is in python2.7:   i type   apt-get install python2.7 Reading package lists... Done 



Building dependency tree

Reading state information... Done python2.7 is already the newest version. 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
  

and here all is right also
  

when i'm running totem  i receive
  Failed to create a GStreamer play object. Please check your GStreamer installation.

---

