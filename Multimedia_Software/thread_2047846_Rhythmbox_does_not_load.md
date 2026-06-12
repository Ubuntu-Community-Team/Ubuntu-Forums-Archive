---
title: "Rhythmbox does not load"
date: 2012-08-25
forum: Multimedia Software
---

### Post by Paresh on 2012-08-25
Rhythmbox was working fine ubtil I tried to install a plugin [https://github.com/srijan/StopAfterCurrentTrack-Plugin-for-Rhythmbox]("https://github.com/srijan/StopAfterCurrentTrack-Plugin-for-Rhythmbox")

But after I installed and tried to activate this, Rhythmbox crashed and would not restart.

I have tried removing the plugin & uninstalling and re-installing RB, but no luck.

This is my error.
```

paresh@desktop:~$ rhythmbox

(rhythmbox:9845): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(rhythmbox:9845): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(rhythmbox:9845): Gtk-CRITICAL **: gtk_grid_attach: assertion `GTK_IS_WIDGET (child)' failed

(rhythmbox:9845): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(rhythmbox:9845): Gtk-CRITICAL **: gtk_ui_manager_get_widget: assertion `GTK_IS_UI_MANAGER (manager)' failed
Segmentation fault (core dumped)

```

Can anyone help?

---

### Post by OzzyFrank on 2012-09-04
I've had exactly the same problem (more or less - the error numbers vary) since not long after upgrading to 12.04. It still worked fine after the upgrade, but after some updates not long after, I could not get it to run anymore. Sometimes, in my Gnome 3 Classic taskbar, a button appears saying "Starting Rhythmbox", but it never does. I've been hoping an update would fix it - and was happy to see a major update to rhythmbox and dependent packages a few weeks later - but it's still failing to load. I even tried deleting its data folders, in case it was a setting or plugin, but that made no difference at all. I'm on a 64-bit system, in case that matters.

---

### Post by OzzyFrank on 2012-09-04
Okay... I just looked up Rhythmbox's options, and thought I'd try to open it with **--disable-plugins** - even though I had previously removed any data folders, like the plugins folder to no avail - and it has loaded. While this isn't a fix, and clearly something is amiss with Rhythmbox, at least you can get it to load with **rhythmbox --disable-plugins** until it's fixed.

Obviously, if you really depend on one or more of the plugins, Rhythmbox will be next to useless, other than being able to play your collection. For me, the main thing is being able to play my playlists, though if I need to attach a media player I won't be able to.

---

### Post by Bolinga on 2012-10-30
Hi! I have the same problem... It started when I upgraded to Ubuntu 12.10, before it worked perfectly. But even now when I open it with "rhythmbox --disable-plugins" it only shows the interface and then it freezes. So it's not really a solution for me :/

I've also tried reinstalling without plugins without any succes.

Any ideas?

---

### Post by Bolinga on 2012-10-31
Oke so for me this helped:
1. open: Synaptic packet manager
2: search: Rhythmbox
3: uninstall all the installed plugins one at the time, untill you've found the trouble maker.

(in my case it was Rhythmbox-radio-browser)
You might reinstall the particular plugin, or search a alternative one.

---

