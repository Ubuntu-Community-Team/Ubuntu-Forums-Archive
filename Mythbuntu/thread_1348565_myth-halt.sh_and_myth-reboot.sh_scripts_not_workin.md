---
title: "myth-halt.sh and myth-reboot.sh scripts not working"
date: 2009-12-07
forum: Mythbuntu
---

### Post by IndieRockSteve on 2009-12-07
$ /usr/share/mythtv/myth-reboot.sh
Error org.freedesktop.DBus.Error.AccessDenied: Rejected send message,
1 matched rules; type="method_call", sender=":1.13" (uid=1000 pid=3142
comm="dbus-send)
interface="org.freedesktop.Hal.Device.SystemPowerManagement"
member="Reboot" error name="(unset)" requested_reply=0
destination="org.freedesktop.Hal" (uid=0 pid=784 comm="hald))

anyone have any ideas why this isn't working?
thanks!

---

### Post by superm1 on 2009-12-07
From where are you running this?

SSH?
Within X Server?
Local console?

I'd only expect from within X server or local console to work.  Most definitely not SSH.

---

