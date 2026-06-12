---
title: "Rhythmbox freezes after starting"
date: 2012-11-17
forum: Multimedia Software
---

### Post by AbdRahim on 2012-11-17
Rhythmbox freezes after starting every time.
Ubuntu 12.04 and 12.10. I did fresh install of 12.10. Rhythmbox worked for a day or so and then froze as usual.
This is the errors opening as sudo in terminal.

(rhythmbox:3232): Rhythmbox-WARNING **: Unable to grab media player keys: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `org.gnome.SettingsDaemon.MediaKeys' on object at path /org/gnome/SettingsDaemon/MediaKeys

** (rhythmbox:3232): WARNING **: Error calling get_info: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (rhythmbox:3232): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

(rhythmbox:3232): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:3232): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:3232): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

---

