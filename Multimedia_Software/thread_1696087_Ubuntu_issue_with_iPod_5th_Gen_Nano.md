---
title: "Ubuntu issue with iPod 5th Gen Nano"
date: 2011-02-26
forum: Multimedia Software
---

### Post by TheBigGloom on 2011-02-26
Hello everyone. I recently bought a 16GB iPod Nano 5th Gen from a friend. It came with a bunch of bad music so I formatted the iPod (using the "format" button after right-clicking the icon on my desktop).  Using Rhythmbox (I tried other programs too), I added my albums to the iPod with success. The songs show up as transferred to the iPod. Now then, when I eject my iPod and go to listen to the music, there are no songs on the iPod.------I tried formatting the iPod once more and got the same end result. After doing this, I seem to have lost or damaged the iPod firmware? The screen is now plain gray and only displays the battery symbol and "Do Not Disconnect" or "Ok To Disconnect". When I eject the iPod and attempt to reset it, it displays the Apple logo and stops there. It returns to the gray screen after reconnected to the USB cord.---------I should also add that when I right click &quot;properties&quot; on the iPod symbol in Rhythmbox, Rhythmbox shuts down immediately. Running with terminal, it displays this...(next post)------------  So first off, how do I go about fixing my iPod firmware? Second off, how can I use my iPod with Ubuntu without issue?  Thanks!

---

### Post by TheBigGloom on 2011-02-26
battosai@Joshs:~$ rhythmbox-------------- ** (rhythmbox:8371): DEBUG: Loading the real store page----------- ** (rhythmbox:8371): DEBUG: navigation requested to [https://one.ubuntu.com/music/store-no-token----------](https://one.ubuntu.com/music/store-no-token----------)  (rhythmbox:8371): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed--------------  (rhythmbox:8371): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed--------------  (rhythmbox:8371): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed---------------  (rhythmbox:8371): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed------------- ** (rhythmbox:8371): DEBUG: navigation requested to [http://stores.7digital.com/default.aspx?shop=480&partner=983------------------](http://stores.7digital.com/default.aspx?shop=480&partner=983------------------)  (rhythmbox:8371): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed-------------  (rhythmbox:8371): GLib-GIO-CRITICAL **: g_file_new_for_uri: assertion `uri != NULL' failed--------------  (rhythmbox:8371): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed------------  (rhythmbox:8371): GLib-GIO-CRITICAL **: g_file_query_exists: assertion `G_IS_FILE(file)' failed---------  (rhythmbox:8371): GLib-GIO-CRITICAL **: g_file_get_parent: assertion `G_IS_FILE (file)' failed-------------  (rhythmbox:8371): GLib-GIO-CRITICAL **: g_file_get_uri: assertion `G_IS_FILE (file)' failed------------  (rhythmbox:8371): Rhythmbox-WARNING **: filesystem root (null) apparently doesn't exist!-------------  (rhythmbox:8371): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed------------  (rhythmbox:8371): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed-----------------  (rhythmbox:8371): Rhythmbox-CRITICAL **: rb_removable_media_source_build_dest_uri: assertion `sane_uri != NULL' failed-------------  (rhythmbox:8371): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed Segmentation fault--------------

---

### Post by TheBigGloom on 2011-02-26
I was having a bit of spacing issues with those last posts.  I should add that I just tried to connect my iPod to iTunes from a different computer. It said that it detected an iPod, but could not detect it properly.

---

### Post by TheBigGloom on 2011-02-27
Please help :/ I spent good money on this iPod...

---

