---
title: "network manager pppoeconf device not managed"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by Hakimjo on 2010-04-30
After the use of pppoeconf, the network manager does not recognise neither the wired nor the wireless connection anymore.  (It nicely did it before that)

I tried to replace the etc/network manager folder with that of a different machine.  Still the same.

What else can I do to reset Network Manager ?

Thanks

---

### Post by Iowan on 2010-04-30
I'm not near an Ubuntu machine at the moment, but check [I]/etc/NetworkManager/nm-system-settings.conf
[/I] Sometimes setting managed=true helps.

---

