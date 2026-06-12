---
title: "Network Manager error, DBUS&lt;=0.60"
date: 2006-04-14
forum: Networking &amp; Wireless
---

### Post by mengqing on 2006-04-14
I tried to install the Network Manager 0.6, and got the following error

checking for DBUS... configure: error: Package requirements (dbus-glib-1 >= 0.60) were not met:

Requested 'dbus-glib-1 >= 0.60' but version of dbus-glib is 0.36.2


can anyone help me.. ?? thx

---

### Post by spd106 on 2006-04-14
Yeah, dbus >=0.60 is in dapper. You need to upgrade.

---

### Post by Jengist on 2006-09-04
Which repositories do I need to enable to get dbus-glib-1?

---

### Post by spd106 on 2006-09-05
This thread discusses Breezy aka Ubuntu 5.10, which did not have dbus 0.60. 

dbus-glib-1 >= 0.60 is in the libdbus-glib-1-2 package, in the official 6.06 repo.

As long as you have an up-to-date Dapper install you should have this package. Network Manager not to mention D-Bus and about hundred other apps depend on this library package.

---

