---
title: "Rhythmbox completely locks up when I attempt to edit ID3 tags"
date: 2011-04-02
forum: Multimedia Software
---

### Post by asuastrophysics on 2011-04-02
Hey guys,

So I'm having a bit of trouble with Rhythmbox. The program has crashed 4 times while simply grouping 12 songs into one album.

The album is Black Sabbath's "We sold our souls to rock n' roll".

If I right-click on the track and hit "Properties", rhythmbox will just freeze for about 5 minutes before bringing up this error window:
```
Error while saving song information.
Internal GStreamer problem; file is a bug
```

Here is the output of Rhythmbox 0.12.8 in terminal, which, unfortunately, doesn't give any information at all on why I have this error:
```
jakob@jake-desktop:~$ rhythmbox
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_type_class_add_private: assertion `private_size > 0' failed
** (rhythmbox:3539): DEBUG: Loading the real store page
** (rhythmbox:3539): DEBUG: navigation requested to https://one.ubuntu.com/music/store-no-token
** (rhythmbox:3539): DEBUG: navigation requested to http://stores.7digital.com/default.aspx?shop=480&partner=983
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:3539): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:3539): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:3539): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

```

Is there a solution to this problem? A better question: Is there a somewhat stable music player on Ubuntu that I can use? Preferably a player that's actually made it to version 1.0? Rhythmbox has been out on Ubuntu for at least 4 years now and in that time it hasn't even gone 1 whole version number. Obviously it is not being developed anymore...

---

### Post by asuastrophysics on 2011-04-12
bump

---

### Post by Yellow Pasque on 2011-04-12
You do have permissions to write to the files, correct?
This one may be of interest: [https://bugzilla.gnome.org/show_bug.cgi?id=577433](https://bugzilla.gnome.org/show_bug.cgi?id=577433)

---

### Post by asuastrophysics on 2011-04-13
> **Temüjin said:**
> You do have permissions to write to the files, correct?
This one may be of interest: [https://bugzilla.gnome.org/show_bug.cgi?id=577433](https://bugzilla.gnome.org/show_bug.cgi?id=577433)

The music folder is located on a different username in the /home directory. I thought I set the permissions correctly, but I'll go back and take another look just to be sure. I'll take a look at that bug report too.

Thanks for your help buddy! :)

---

