---
title: "Xubuntu 18.04.2 - Clementine install kills keyboard"
date: 2019-04-01
forum: Multimedia Software
---

### Post by guitarguy123872 on 2019-04-01
Hello,

I've been using Xubuntu for a while now and have been generally quite happy with it. However, I have recently run across a really strange issue. I installed clementine via apt-get (well actually, this is an offline server so I use apt-medium to pull down the necessary packages from another PC and copy/install them on this PC. apt-get still manages them, though. I've had no issues using this same process with all kinds of other software so I don't think it is inherently the issue). Immediately after the install (i.e. no reboot), everything works fine, including clementine. When I reboot, suddenly the keyboard stops working in all my apps. In a terminal, the prompt just flashes whenever i press any key. Strangely, it still works at the login screen. As soon as I un-install clementine, everything is fine again.

I'm not really sure how to even debug this. I have noticed some errors related to xfce4 in .xsession_errors like:
```
ERROR:dbus.proxies:Introspect error on org.bluez:/:  dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied:  Rejected send message, 2 matched rules; type="method_call",  sender=":1.57" (uid=1000 pid=1738 comm="/usr/bin/python3  /usr/bin/blueman-applet " label="unconfined")  interface="org.freedesktop.DBus.Introspectable" member="Introspect"  error name="(unset)" requested_reply="0" destination="org.bluez" (bus)
```


but I'm not 100% sure they're related. Any ideas how I can figure this out?



Thanks!

---

