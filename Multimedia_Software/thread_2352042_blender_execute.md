---
title: "blender execute"
date: 2017-02-09
forum: Multimedia Software
---

### Post by satimis on 2017-02-09
Hi all,

Vm - blender-2.7.0
Oracle Virtualbox

Blender is installed on /home/username/blender-2.7.0  It can be started on terminal running;```

/home/username/blender-2.7.0/blender

```

But I couldn't find/execute it on Dash

Running gconf-editor
I can't find unity under desktop only gnome

Please advise how to add blender to Dash?

Thanks

Regards
satimis

---

### Post by Perfect Storm on 2017-02-09
You can use **alacarte** or **menulibre** to make an entry for blender.

---

### Post by satimis on 2017-02-09
> **Artificial Intelligence said:**
> You can use **alacarte** or **menulibre** to make an entry for blender.
Hi,

Thanks for your advice.

On terminal started alacarte

-> New Item
Name: Blender
Command: /home/username/blender-2.7.0/blender
Comment: blank
Check Launch on Terminal? (also tried without check)
-> OK
```

/usr/share/alacarte/Alacarte/MainWindow.py:22: PyGIWarning: GMenu was imported without specifying a version first. Use gi.require_version('GMenu', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GdkPixbuf, Gdk, GMenu

(alacarte:8136): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion 'gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(alacarte:8136): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion 'gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

```

On Dash
3 blenders are found there but without icon
(please see attached photo)

Clicking any of them will start "Blender" with icon displayed on the launcher.  But exit "Blender" the icon on the launcher will exit as well.  Lock to Launcher without effect.

Regards
satimis

---

### Post by Perfect Storm on 2017-02-09
you can set icon in alacarte or at least you can do it with libremenu (which I use).
Sorry I can't be more helpful as I don't have a machine with unity on them to test it.

---

