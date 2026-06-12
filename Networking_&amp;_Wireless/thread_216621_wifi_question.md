---
title: "wifi question"
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by VoodooSmurf on 2006-07-15
I have been running ubuntu for about a week now, and just got my wireless working, now that it works, it's signal will eventually fall out, disconnect, then it will come back up.  Is there any way to keep the connection from dropping like that?  It does it like every 1-2 min.  Not a very bad problem, just annoying sometimes...  any help would be appreciated

---

### Post by tturrisi on 2006-07-16
Try changing the channel via the access point, there could be interference from other devices, lights, cables, etc.  Channels 1. 7 & 11 are usually the cleanest.

---

### Post by morequarky on 2006-07-16
Also make sure your access point is set to "renew" the connections every day not every few minutes or hours.

---

### Post by spd106 on 2006-07-16
If you are using an atheros based nic then be aware that the old madwifi driver must lose it's connection to allow for network scans. Sadly Network-Manager does this every two minutes. That (and i'm too lazy to compile madwifi-ng) is the only thing stopping me from using it on my laptop.

> Channels 1. 7 & 11 are usually the cleanest.

Channels 1,6 & 11 are the "non-overlapping" channels used in the 2.6GHz band

---

