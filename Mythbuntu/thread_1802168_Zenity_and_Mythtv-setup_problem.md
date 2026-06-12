---
title: "Zenity and Mythtv-setup problem"
date: 2011-07-11
forum: Mythbuntu
---

### Post by LowSky on 2011-07-11
Anyone know what the hell Zenity has to do with MythTv's Backend??? I really need to change some backend stuff and I can't figure it out.

```
john@mediacenter:~$ mythtv-setup

** (zenity:11158): WARNING **: Could not load ui file /usr/share/zenity/zenity.ui: Failed to open file '/usr/share/zenity/zenity.ui': No such file or directory

(zenity:11158): Gtk-CRITICAL **: IA__gtk_builder_get_object: assertion `GTK_IS_BUILDER (builder)' failed

(zenity:11158): Gtk-CRITICAL **: IA__gtk_builder_get_object: assertion `GTK_IS_BUILDER (builder)' failed
john@mediacenter:~$ 

```

P.S. The frontend is working fine.

---

### Post by LowSky on 2011-07-11
Fixed by grabbing the entire /usr/share/zenity folder from another PC. Really odd issue.

---

### Post by craigsq on 2011-08-10
Had the same issue, fixed by doing a reinstallation of zenity in synaptic package manager

---

