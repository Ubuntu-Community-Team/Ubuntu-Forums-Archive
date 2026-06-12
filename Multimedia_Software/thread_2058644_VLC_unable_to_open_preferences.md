---
title: "VLC unable to open preferences"
date: 2012-09-16
forum: Multimedia Software
---

### Post by toraias on 2012-09-16
Hi,

I have recently moved form Opensuse to Ubuntu 12.10 beta and tried using VLC. The Preferences windows goes crazy. I am not able to open it and it crashed compiz one time.

The error appears with 2.0 version as well as with 2.1 beta

running on console shows: 

```
(vlc:5378): Gtk-CRITICAL **: IA__gtk_widget_style_get: assertion `GTK_IS_WIDGET (widget)' failed

(vlc:5378): Gtk-CRITICAL **: IA__gtk_widget_style_get: assertion `GTK_IS_WIDGET (widget)' failed
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0

```

I have found on launchpad that it seems a Unity bug, anyone having a workaround?

---

