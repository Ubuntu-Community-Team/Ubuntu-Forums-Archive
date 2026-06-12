---
title: "Zattoo suddenly segfaults"
date: 2010-06-13
forum: Multimedia Software
---

### Post by mrowth on 2010-06-13
Zattoo (TV watching application, see [http://zattoo.com/](http://zattoo.com/) ) used to work fine until... a couple days ago, presumably. Now the window vanishes again before anything appears other than the menu bar. From KPackagekit's history I can tell there were updates to ligbail18, libtk2.0-common. libgtk2.0-0, libgtk2.0-bin and others on Tuesday 08 June 2010 but I don't know if that was it. 

```
$ Zattoo 

(process:17833): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.24.1/gobject/gtype.c:2706: You forgot to call g_type_init()

(process:17833): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:17833): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
Segmentation fault
```

(I'm prefixing this as "all variants" because Zattoo is not a Kubuntu-specific application; however, I'm using Kubuntu 10.04 32 bit with KDE 4.4.85 (beta of KDE 4.5). Flash is at version 10.1.53.64.)

---

### Post by gepomuk on 2010-06-14
Got the same problem, Kubuntu as well. Same flash version, but stable KDE 4:4.4.2.
Reinstall of Zattoo does not change anything. Zattoo is a bit ominous anyway, isn't it? However it would be nice to get it working again, maybe there was something wrong with one of the most recent updates? Say during the last two weeks or so.

---

### Post by mrowth on 2010-06-16
> **gepomuk said:**
> Got the same problem, Kubuntu as well. Same flash version, but stable KDE 4:4.4.2.
Reinstall of Zattoo does not change anything. Zattoo is a bit ominous anyway, isn't it? However it would be nice to get it working again, maybe there was something wrong with one of the most recent updates? Say during the last two weeks or so.

Dunno if it's ominous. Don't like the ads, of course, but then again I'm not forced to use it. I've sent them a problem report, though the contact form seems to be for the website only. Ahwell. Not expecting anything...

---

### Post by gepomuk on 2010-06-20
Yeah, not expecting anything was exactly the right thing to do. In their FAQ the zattoo folks state that linux is no longer supported and we should watch by browser. Just tried this, works even worse than with the application. As you said: I don't have to use it, so I won't anymore.

---

### Post by immerblau on 2011-03-28
"[QUOTE=mrowth;9456827]Zattoo (TV watching application, see [http://zattoo.com/](http://zattoo.com/) ) used to work fine until... a couple days ago, presumably. Now the window vanishes again before anything appears other than the menu bar. From KPackagekit's history I can tell there were updates to ligbail18, libtk2.0-common. libgtk2.0-0, libgtk2.0-bin and others on Tuesday 08 June 2010 but I don't know if that was it." 

The problem seems to still exist (March 2011). I recently installed 10.10, next to Vista. To access Zattoo I've always used Google Chrome or Firefox browser. No problem. - Now with 10.10, however, I cannot get past Zattoo's program guide: no connection with the selected TV station, no sound. I tried Google Chrome as well as Firefox. I guess the problem is not with Zattoo but Ubuntu. - Restarting my laptop and selecting Vista I can watch TV with Zattoo.

---

