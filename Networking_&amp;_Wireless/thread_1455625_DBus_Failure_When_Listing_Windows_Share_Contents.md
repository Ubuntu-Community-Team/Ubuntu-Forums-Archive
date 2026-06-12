---
title: "DBus Failure When Listing Windows Share Contents"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by iposner on 2010-04-16
I can view the Windows shares on a ReadyNas NV+ (Debian Sarge under the covers). However when I double-click the share in nautilus, I get the following error:

**Unable to mount location**
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus).

This is after a complete re-installation of the Beta 2, only maintaining the home directory which is located on a separate partition.

Note that this is a wired networking connection.

Strangely the same Lucid Lynx version and Windows 7 can enumerate all the files/folders within the share when run from a different x64 computer.

So the problem is caused either by hardware differences, or the contents of the .dbus folder for each user.

Does anybody know whether the contents of the .dbus folder can be deleted and whether new files are generated?


Lucid Lynx 10.04 Beta 2 x64.

---

