---
title: "How to get network icon on task bar back?"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by Jordanhawks on 2010-06-22
Got rid of the network icon on task bar, how can
I get it back?

---

### Post by jxtreme on 2010-06-22
It's called the panel in Ubuntu. Go to System>Preferences>Startup Applications. If the Network Manager is not there, click add and name it whatever, and paste in the command:
```
nm-applet --sm-disable
```then click add. Restart and  you should see the network manager applet.

---

### Post by Iowan on 2010-06-22
Sometimes NM will return if you add a "Notification area" to your panel.

---

