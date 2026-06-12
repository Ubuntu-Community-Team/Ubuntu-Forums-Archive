---
title: "movieplayer won't start"
date: 2011-01-27
forum: Multimedia Software
---

### Post by doubleOh on 2011-01-27
my movieplayer won't start up completely and when i try playing videos on vlc-media player it shows a blank screen but i can hear sound from the video file.
how can i fix this? please help

---

### Post by ajgreeny on 2011-01-27
Start movie-player from a terminal with command ```
totem
``` and report back any errors.

Do the same for ```
vlc
``` and see what errors emerge for that as well.

---

### Post by doubleOh on 2011-01-28
**when i start movieplayer from terminal it gives this error message;**


(totem:3871): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(totem:3871): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed

(totem:3871): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed

(totem:3871): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

**and vlc gives this message:**

VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x89aa914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb744d0d4, 0xb744d048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1296317406)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:3908): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)


thanks :)

---

