---
title: "Brasero segfault on Jaunty"
date: 2009-05-10
forum: Multimedia Software
---

### Post by Thorzilla on 2009-05-10
Every time I try to create a new Audio Disc project using brasero on Jaunty after the new upgrades, it crashes.

Here's a dump of the errors:
```
neptune@neptune-laptop:~$ brasero

(brasero:20123): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(brasero:20123): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(brasero:20123): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(brasero:20123): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GstElement'

(brasero:20123): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(brasero:20123): GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(brasero:20123): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(brasero:20123): GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(brasero:20123): GStreamer-CRITICAL **: gst_bin_remove: assertion `GST_IS_ELEMENT (element)' failed

(brasero:20123): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GstElement'

(brasero:20123): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(brasero:20123): GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(brasero:20123): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(brasero:20123): GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Segmentation fault

```

I'm running Ubuntu 9.04  on a Sony Vaio FW series

The syslogs have this:

```
ay 10 10:30:00 neptune-laptop kernel: [61065.055422] brasero[13529]: segfault at ffffffff ip b72a1c95 sp bfeed5d0 error 4 in libglib-2.0.so.0.2000.1[b724a000+b6000]
May 10 10:30:01 neptune-laptop /USR/SBIN/CRON[14608]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May 10 10:30:12 neptune-laptop kernel: [61077.143173] brasero[15065]: segfault at 0 ip b70f174f sp bfeeac3c error 6 in libpthread-2.9.so[b70e7000+15000]
May 10 10:30:24 neptune-laptop kernel: [61089.252715] brasero[17955]: segfault at ffffffff ip b73a9bcb sp b4cfda00 error 4 in libglib-2.0.so.0.2000.1[b7351000+b6000]
May 10 10:30:43 neptune-laptop kernel: [61108.238623] brasero[20707]: segfault at ffffffff ip b7294bcb sp b4498a00 error 4 in libglib-2.0.so.0.2000.1[b723c000+b6000]
```

---

