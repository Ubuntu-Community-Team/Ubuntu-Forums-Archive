---
title: "Can't Connect to Internet after install of 9.04"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by richdb on 2009-10-21
After upgrading to Ubuntu 9.04, firefox is unable to access internet even though networking says I'm connected to my wireless router. No problem before upgrade.

---

### Post by Iowan on 2009-10-21
Hopefully yours isn't one of those cards that lost support. Wait, that was ATI video...
Check **ifconfig -a**. It will probably show IP address for wireless.  Another thing will be to check **route -n** to verify the router shows up as default gateway. */etc/resolv.conf* should contain the names of your DNS servers.

---

