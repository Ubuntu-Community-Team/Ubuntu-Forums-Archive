---
title: "auto run '/usr/bin/portal'after the system start"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by Under Tree on 2009-05-12
'/usr/bin/portal'is used to connect to our local network.
how can i set it auto run after system start and get an ip under dhcp?:confused:

---

### Post by chili555 on 2009-05-12
I'm not familiar with portal, but it seems you should be able to call whatever commands you run manually by amending */etc/rc.local*. For example:```
portal -[OPTIONS]
dhclient wlan0
```Modify to suit.

---

