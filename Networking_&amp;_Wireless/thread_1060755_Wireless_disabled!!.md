---
title: "Wireless disabled!!"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by xannaxprozaxx on 2009-02-05
I'm a girl and my brother convinced me to install ubuntu and I know nothing about it so you have to go slowly on me :).
I have a toshiba satelite A-200. I had a fresh installation of Ubuntu 2 days ago, and everything was going fine, but after updating, my wireless icon disappeared and I can't connect anymore. I tried following the instructions in the provided Ubuntu help and I also searched the forum but to no avail. I have a dual-boot and on windows xp the wireless works fine so it's not a hardware issue. When I try to run nm-applet it tells me:

(nm-applet:5741): applet_dbus_manager_start_service(): could not acquire the NetworkManagerUserSettings service as it is already taken"..." 

PLEASE help!! Thank you in advance!

---

### Post by xannaxprozaxx on 2009-02-06
plz someone help me!

---

### Post by lakersforce on 2009-02-06
Kill the nm-applet process, before you start it up again...

also do

```
lspci
```

at terminal and paste here.

---

### Post by superprash2003 on 2009-02-06
post outpt of **lshw -C network** from the terminal(APplications->accessories->terminal)

---

