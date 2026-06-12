---
title: "Avidemux 8 and 9 keys not working"
date: 2008-07-26
forum: Multimedia Software
---

### Post by Pigeon. on 2008-07-26
It is no longer possible to type the digits 8 or 9 in the "Shift", "Frame" or "Time" fields on the main window of avidemux.

This follows an upgrade from fluxbuntu gutsy to hardy - which also clobbered /etc/alternatives/x-session-manager symlink and pointed it at startkde instead of startfluxbox... It was fine until I rebooted, only after the reboot did 8 and 9 stop working.

In order to go to a frame whose number includes those digits I have to use the Go to Frame... dialog from the Go menu.

This is happening both in the latest hardy version of avidemux (2.4.1) and in 2.4 (r3731) installed in /usr/local/bin.

You can still type * and ( in the fields where 8 and 9 do not work.

8 and 9 work fine in the various dialogues of avidemux, it's only the fields on the main window which don't work. They seem to work fine in every other app too.

---

### Post by Pigeon. on 2008-07-26
...The Qt version doesn't do it. But the Qt version is not a suitable substitute because it does not have the jog wheel.

---

