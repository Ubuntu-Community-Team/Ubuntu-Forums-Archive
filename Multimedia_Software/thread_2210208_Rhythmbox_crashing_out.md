---
title: "Rhythmbox crashing out"
date: 2014-03-09
forum: Multimedia Software
---

### Post by Tony_Pickett on 2014-03-09
I'm running Rhythmbox 2.99.1 on Xubuntu 13.10

I have my library and that seems to be fine, there seems to be no issue finding tracks, and it plays just fine - except ...

Every now and again it crashes out when moving from one track to the other.
I'm not sure I've ever seen a log file for Rythmbox so I ran it from a terminal and these were the messages I got:

```

tony@Alice:~/Desktop$ rhythmbox

(rhythmbox:10549): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(rhythmbox:10549): GLib-GObject-CRITICAL **: Custom constructor for class SoupServer returned NULL (which is invalid).  Unable to remove object from construction_objects list, so memory was probably just leaked.  Please use GInitable instead.

(rhythmbox:10549): Rhythmbox-WARNING **: Unable to grab media player keys: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SettingsDaemon was not provided by any .service files
Segmentation fault (core dumped)
tony@Alice:~/Desktop$ 










(rhythmbox:11812): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(rhythmbox:11812): GLib-GObject-CRITICAL **: Custom constructor for class SoupServer returned NULL (which is invalid).  Unable to remove object from construction_objects list, so memory was probably just leaked.  Please use GInitable instead.

(rhythmbox:11812): Rhythmbox-WARNING **: Unable to grab media player keys: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SettingsDaemon was not provided by any .service files
Segmentation fault (core dumped)
tony@Alice:~/Desktop$ 

```

I see that it appears to be looking for Gnome and I'm using XFCE - any clue why it would be looking for gnome stuff?
Any thoughts on what is happening - I've used this Rhythmbox/xfce combination on other computers for several years now with no issues.

---

### Post by Yellow Pasque on 2014-03-09
IIRC, this can happen if gapless playback is enabled. I can't find the exact bug report for that at the moment, but I would suggest disabling it and seeing if issue still occurs.

---

### Post by Tony_Pickett on 2014-03-10
Thanks - I did check and no I don't have that enabled.
It's odd, it has never done this to me in all the years I have used Rhythmbox - it has always been rock solid.

---

### Post by Yellow Pasque on 2014-03-10
So have you reported it using apport? [https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)

---

### Post by Tony_Pickett on 2014-03-10
Yes, I have.
Did it again, just to make sure.

---

