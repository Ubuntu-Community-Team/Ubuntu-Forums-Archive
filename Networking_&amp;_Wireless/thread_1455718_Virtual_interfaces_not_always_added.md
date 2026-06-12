---
title: "Virtual interfaces not always added"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by v8YKxgHe on 2010-04-16
Morning,

I've added many virtual interfaces to eth0 via /etc/network/interfaces using 'up ip addr add ...', however when doing '/etc/init.d/networking restart' not all aliases/virtual interfaces are added. Some of them are and some aren't.

I really can't see what is causing it, as copying the 'ip addr add' command in that file, and running it adds the virtual interface just fine.

This is quite annoying as when the server restarts, we're missing IP addresses.

Regards,

---

