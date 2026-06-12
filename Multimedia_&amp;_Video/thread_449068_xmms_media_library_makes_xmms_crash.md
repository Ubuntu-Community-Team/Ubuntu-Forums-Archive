---
title: "xmms media library makes xmms crash"
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by Hildsvfar on 2007-05-19
I compiled this from source [http://xpg.dk/projects/xmms-media-library/](http://xpg.dk/projects/xmms-media-library/) then when I enabled it in xmms it crashed. when I reopened xmms again, it crashed.  If I open xmms it crashes just because of this plugin.  I don't know how to uninstall the plugin, or just disable it without even opening the program, because it crashes too fast to give me a chance to disable it.  Here's what happens every time I open xmms

Gtk-CRITICAL **: file gtkwidget.c: line 3178 (gtk_widget_grab_default): assertion `GTK_WIDGET_CAN_DEFAULT (widget)' failed.
Message: device: default
*** glibc detected *** double free or corruption (fasttop): 0x08250a10 ***
Aborted

---

### Post by Hildsvfar on 2007-05-21
No one has any idea how to fix my problem?  I even tried complete removal of xmms, then installing it again but the media library thing still opened becuase I'm not really sure how to remove it since it's compiled from source

---

### Post by Hildsvfar on 2007-05-23
Nevermind, I just edited the xmms config file and removed the part about the media library

---

