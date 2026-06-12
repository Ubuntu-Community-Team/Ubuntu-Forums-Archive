---
title: "Turning off Network connection ballon"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by jjjjeremy on 2010-02-16
Hey,

I've searched many forums, and I can't find out how to turn off the wireless connection balloons. I regularly switch between wireless networks, and it's really annoying to have two connect/disconnect notifications each time that I switch between networks.

Any way to turn this off? Well, I know that there always *is* a way to turn it off, I just need to find it.

---

### Post by sinter on 2010-02-17
```
sudo mv  /usr/share/dbus-1/services/org.freedesktop.Notifications.service  /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled  
```

This disables all notification messages in Ubuntu.

---

### Post by jjjjeremy on 2010-02-22
That just renames the notification file.

---

