---
title: "Autostart wlan0 on boot"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by Torn on 2011-04-04
I have an Ubuntu server installed at home, on an older machine. Unfortunately I am to far from my router to run cat5 and solve this issue. But I want to be able to have the wireless come up if the server restarts as then i could log in remotely.

Thank you.

---

### Post by mikewhatever on 2011-04-04
Try adding the following to /etc/rc.local, before the 'exit 0' line':

```
ifconfig wlan0 up
```

---

