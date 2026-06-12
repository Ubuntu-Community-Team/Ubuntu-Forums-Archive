---
title: "No network connection"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by russell.dexter on 2010-10-04
Fresh install of 10.04, but no network connection available. Did a sudo dhclient and got a 'no broadcast interfaces found.' Any ideas?

---

### Post by rangupraveen on 2010-10-04
I had the same problem when I installed this Saturday.

All you need to do is connect your LAN cable and then you will be on Internet. Upgrade by downloading all the updates, and this will activate your wireless connection.

Have fun with Ubuntu :)

---

### Post by dineshs on 2010-10-05
Please post the results of the following terminal command(applications-accessories -terminal)
```
sudo lshw -C network
```

---

