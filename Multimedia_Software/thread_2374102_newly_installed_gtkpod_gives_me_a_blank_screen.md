---
title: "newly installed gtkpod gives me a blank screen"
date: 2017-10-12
forum: Multimedia Software
---

### Post by pjstock on 2017-10-12
I am trying to use GTKPod for the first time with Ubuntu 16.04 LTS.

It seems to startup, then shows "importing configured Ipods" in the Lower LH corner. then shows "Importing of Ipods complete"
and then nothing, just a blank screen. (see attached screenshot)
any suggestions?

---

### Post by kostkon on 2017-10-12
Try running it from the terminal, see if you'll get any error messages.

---

### Post by pjstock on 2017-10-13
I get:
peter@CollierDesk:~$ gtkpod

(gtkpod:2169): GLib-GObject-CRITICAL **: g_value_type_transformable: assertion 'G_TYPE_IS_VALUE (src_type)' failed

(gtkpod:2169): Gtk-WARNING **: /build/gtk+3.0-QpXqW7/gtk+3.0-3.18.9/./gtk/gtkliststore.c:836: Unable to convert from (null) to gchararray


(gtkpod:2169): GLib-GObject-CRITICAL **: g_value_type_transformable: assertion 'G_TYPE_IS_VALUE (src_type)' failed

(gtkpod:2169): Gtk-WARNING **: /build/gtk+3.0-QpXqW7/gtk+3.0-3.18.9/./gtk/gtkliststore.c:836: Unable to convert from (null) to gchararray


(gtkpod:2169): GVFS-RemoteVolumeMonitor-WARNING **: remote volume monitor with dbus name org.gtk.vfs.UDisks2VolumeMonitor is not supported
^C
peter@CollierDesk:~$ 

which means nothing to me unfortunately.....

---

