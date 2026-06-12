---
title: "Flash Plugin Errors - Gtk-CRITICAL errors"
date: 2013-01-21
forum: Multimedia Software
---

### Post by sparek-3 on 2013-01-21
I've pulled out every hair on my head trying to figure this one out.

I have verified that Flash is installed with **about:plugins**

I can't get Flash to work in FireFox on Ubuntu 12.04.  When I try to load a test flash page like:

[http://helpx.adobe.com/flash-player/kb/find-version-flash-player.html](http://helpx.adobe.com/flash-player/kb/find-version-flash-player.html)

It just shows a black box where the flash contents is suppose to be.

The console shows the errors:

```
(plugin-container:2551): Gtk-CRITICAL **: IA__gtk_widget_get_visual: assertion `GTK_IS_WIDGET (widget)' failed

(plugin-container:2551): Gdk-CRITICAL **: IA__gdk_colormap_new: assertion `GDK_IS_VISUAL (visual)' failed

(plugin-container:2551): Gdk-CRITICAL **: IA__gdk_colormap_alloc_colors: assertion `GDK_IS_COLORMAP (colormap)' failed

(plugin-container:2551): Gtk-CRITICAL **: IA__gtk_widget_modify_bg: assertion `GTK_IS_WIDGET (widget)' failed

(plugin-container:2551): Gtk-CRITICAL **: IA__gtk_widget_get_visual: assertion `GTK_IS_WIDGET (widget)' failed

(plugin-container:2551): Gdk-CRITICAL **: IA__gdk_colormap_new: assertion `GDK_IS_VISUAL (visual)' failed

(plugin-container:2551): Gdk-CRITICAL **: IA__gdk_colormap_alloc_colors: assertion `GDK_IS_COLORMAP (colormap)' failed

(plugin-container:2551): Gtk-CRITICAL **: IA__gtk_widget_modify_bg: assertion `GTK_IS_WIDGET (widget)' failed

(plugin-container:2551): Gtk-CRITICAL **: IA__gtk_widget_get_visual: assertion `GTK_IS_WIDGET (widget)' failed

(plugin-container:2551): Gdk-CRITICAL **: IA__gdk_colormap_new: assertion `GDK_IS_VISUAL (visual)' failed

(plugin-container:2551): Gdk-CRITICAL **: IA__gdk_colormap_alloc_colors: assertion `GDK_IS_COLORMAP (colormap)' failed

(plugin-container:2551): Gtk-CRITICAL **: IA__gtk_widget_modify_bg: assertion `GTK_IS_WIDGET (widget)' failed

(plugin-container:2551): Gtk-CRITICAL **: IA__gtk_widget_get_visual: assertion `GTK_IS_WIDGET (widget)' failed

(plugin-container:2551): Gdk-CRITICAL **: IA__gdk_colormap_new: assertion `GDK_IS_VISUAL (visual)' failed

(plugin-container:2551): Gdk-CRITICAL **: IA__gdk_colormap_alloc_colors: assertion `GDK_IS_COLORMAP (colormap)' failed

(plugin-container:2551): Gtk-CRITICAL **: IA__gtk_widget_modify_bg: assertion `GTK_IS_WIDGET (widget)' failed

(plugin-container:2551): Gtk-CRITICAL **: IA__gtk_widget_get_visual: assertion `GTK_IS_WIDGET (widget)' failed

(plugin-container:2551): Gdk-CRITICAL **: IA__gdk_colormap_new: assertion `GDK_IS_VISUAL (visual)' failed

(plugin-container:2551): Gdk-CRITICAL **: IA__gdk_colormap_alloc_colors: assertion `GDK_IS_COLORMAP (colormap)' failed

(plugin-container:2551): Gtk-CRITICAL **: IA__gtk_widget_modify_bg: assertion `GTK_IS_WIDGET (widget)' failed
```I have no idea what package I'm missing.  I'm assuming that is the issue.

I did have Flash working, but I had to reinstall Ubuntu 12.04, and now this is my issue.  I know Flash will work with FireFox on 12.04, but I have no clue why it's not now.

---

### Post by Lightning Dragon on 2013-01-21
Hello,

Go to  your distro's software center and search up "flash" or "adobe flash". If you see them, install them and restart Firefox and see if that works.

---

### Post by sparek-3 on 2013-01-23
The flash plugin is installed.  Any other suggestions?

---

### Post by sparek-3 on 2013-01-23
Apparently the issue was bad permissions on some shared libraries.  In my case the specific library was:

/lib/i386-linux-gnu/librtmp.so.0

Should be set to 644.

---

### Post by dirkd on 2013-12-24
I had issues with the same library. After updating from 10.04 to 12.04 LTS two problems were encountered:
* flash didn't work with firefox anymore,
* virtualbox refused to start.

Both problems were resolved by copying /usr/lib/i486-linux-gnu/librtmp.so.0 to
* /usr/lib/firefox
* /usr/lib/virtualbox

I didn't have to change permissions.

Maybe I could have just moved it to /usr/lib/i386-linux-gnu, but I didn't experiment with that.

---

