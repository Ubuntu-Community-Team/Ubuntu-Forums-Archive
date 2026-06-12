---
title: "Internet Video - I wish it worked"
date: 2010-07-05
forum: Multimedia Software
---

### Post by elvinatom on 2010-07-05
I run a MythTV backend/frontend PC in my living room. My Internet Video pluging is crashing the frontend every time I select a search result, giving glib errors.  My Mythbuntu 10.04 was upgrade several times and some other minor problems crept in over time, so I did a fresh install: Ubuntu 10.04 i386, then updates, then mythbuntu-desktop on top.  nfs shares and video driver were added after that but no codecs, no tweaks, no other extras of any kind.  Same result: Click and crash.  Sometimes I can see something entering into fullscreen with a progress bar at about 10-20% for about 1-2 seconds before the crash happens.

On another frontend it does the exact same thing, running Archlinux AMD64 + MythTV.  No problem playing back flash content under firefox though ... strange.

Does anybody know how to find the reason (and maybe solution) for the crash?  Other people seem to have no problems with the new plugin.  Both PCs run Athlon X2 with 2GB RAM and have a (different) nvidia based board and nvidia pcix video card installed.
```

(process:3149): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.24.1/gobject/gtype.c:2706: You forgot to call g_type_init()

(process:3149): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:3149): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
Segmentation fault
```

---

### Post by elvinatom on 2010-07-06
bump, does really nobody else have this behavior?

---

### Post by Kidwell on 2010-09-01
I have the same problem after updating. Let the investigation begin. :popcorn:

---

