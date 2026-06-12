---
title: "funny behaviour of webcam on kubuntu and ubuntu"
date: 2008-04-03
forum: Multimedia &amp; Video
---

### Post by ankscorek on 2008-04-03
helo friends

im using kubuntu and ubuntu 7.10 on x86 64 bit arch

i have installed cheese and kopete in both

**_this is what happens in kubuntu_**

[COLOR="DarkRed"]cheese
** Message: Probing the webcam, please ignore the following, not applicabable tries
using source: v4l2src

(cheese:7045): GStreamer-CRITICAL **: gst_bin_add: assertion `GST_IS_ELEMENT (element)' failed

(cheese:7045): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

       ---------------------- DirectFB v0.9.25 ---------------------
             (c) 2000-2002  convergence integrated media GmbH
             (c) 2002-2004  convergence GmbH
        -----------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2007-08-07 19:24)
(*) Direct/Memcpy: Using SSE optimized memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!

** (cheese:7045): CRITICAL **: gst_x_overlay_set_xwindow_id: assertion `overlay != NULL' failed
[/COLOR]


if i use kopete and send webcam to my friends im able to do it successfully

[B][U]
this is what happened in ubuntu[/U][/B]

cheese runs fine

however when i try to send webcam on kopete to my friends it is unable to show my display image also



where is the problem?
pl help?

---

