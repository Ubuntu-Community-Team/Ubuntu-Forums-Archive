---
title: "Problems with brasero"
date: 2009-01-02
forum: Multimedia Software
---

### Post by Jordanwb on 2009-01-02
Is it just me or is 64 bit brasero-0.8.2 buggy? When I try to make an Audio CD it freezes and I can't get it to respond. Sometimes it closes all by itself with no crash report.

---

### Post by wolfen69 on 2009-01-02
0.8.2 works for me. you could always try K3B for burning. one of my favs.

---

### Post by ricardisimo on 2009-01-04
k3b is the way to go. Why anyone else bothers is beyond me (although if someone wanted to integrate a disc cover printing function for k3b like brasero's, that would be great.)

Here's what's going on when I try to run brasero:

```
~$ brasero

(brasero:27190): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' failed

(brasero:27190): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(brasero:27190): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(brasero:27190): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(brasero:27190): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GstElement'

(brasero:27190): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(brasero:27190): GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(brasero:27190): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(brasero:27190): GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(brasero:27190): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GstElement'

(brasero:27190): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(brasero:27190): GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(brasero:27190): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(brasero:27190): GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Segmentation fault
```
I'm going to check launchpad as well.

---

### Post by Jordanwb on 2009-01-04
A segmentation fault doesn't sound good to me.

---

### Post by zeronothing on 2009-01-04
you could try downloading the newest version of brasero from getdeb [[COLOR="Blue"]website[/COLOR]]("www.getdeb.net"). the .deb package is available is only available for ubuntu 8.10. the version they have is 0.8.4.

---

