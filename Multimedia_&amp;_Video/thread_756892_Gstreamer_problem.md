---
title: "Gstreamer problem"
date: 2008-04-16
forum: Multimedia &amp; Video
---

### Post by Chrysophylax on 2008-04-16
Hey!
I've got a sound issue I hope you guys could help me with. Basically the problem is with gstreamer and I can't hear any sound in some applications. Systeme sounds are ok (when I test it in the preferences menu) and applications like VLC works properly. 

I don't have sounds for Pidgin and when running through the terminal and trying to run the sound test in Tools>Preferences>Sound, i get following error message in the console:

"(pidgin:6470): GStreamer-CRITICAL **: gst_bin_add: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:6470): GStreamer-CRITICAL **: gst_element_link_pads: assertion `GST_IS_ELEMENT (dest)' failed

(pidgin:6470): GStreamer-CRITICAL **: gst_element_link_pads: assertion `GST_IS_ELEMENT (src)' failed
"

Doing the same for rhytmbox i get:

"(rhythmbox:6740): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(rhythmbox:6740): GStreamer-CRITICAL **: gst_bin_add: assertion `GST_IS_ELEMENT (element)' failed

(rhythmbox:6740): GStreamer-CRITICAL **: gst_element_link_pads: assertion `GST_IS_ELEMENT (dest)' failed

(rhythmbox:6740): GStreamer-CRITICAL **: gst_element_link_pads: assertion `GST_IS_ELEMENT (src)' failed

(rhythmbox:6740): RhythmDB-CRITICAL **: rhythmdb_entry_get_string: assertion `entry != NULL' failed
"

Now it seems that a lot of applications depends of gstreamer, like ubuntu-desktop, so I think its not a good idea to remove it directly but i'm not so experienced..

That's it!

---

