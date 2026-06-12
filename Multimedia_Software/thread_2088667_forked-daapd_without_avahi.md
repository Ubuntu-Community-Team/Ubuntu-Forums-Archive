---
title: "forked-daapd without avahi"
date: 2012-11-27
forum: Multimedia Software
---

### Post by vixducis on 2012-11-27
I'm trying to setup forked-daapd, but i'd prefer it if i could run it without avahi (or rather define my own avahi service instead of using the dbus api). 

The reason is that i want a netatalk share for my time machine backups and a samba share for the symbolic link support (netatalk doesn't support symlinks). Those two are defined as different services in avahi. To make that work, i have to disable avahi's dbus api, or else netatalk tends to take over all the services (osx prefers afp over smb).

If I now try to start forked-daapd, it just doesn't. Forked-daapd requires avahi's dbus api to be enabled and running. Is there some sort of way around this limitation, so that i can manually define my own daap service in avahi.

Maybe something like enabling but ignoring the dbus in avahi, or launching a duplicate avahi daemon with a different config file?

---

