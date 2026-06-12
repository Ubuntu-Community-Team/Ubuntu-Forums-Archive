---
title: "Automatically Connect to Internet on Startup"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by moo-cow on 2006-06-01
Since I ran dslconfig to configure a second connection (PPPoE), Ubuntu no longer automatically establishes my primary connection on startup which is DHCP. I now have to `sudo dhclient' to do that. What is the most elegant way to make Ubuntu automatically connect via DHCP on startup?

Thx!
moo-cow

---

### Post by Iowan on 2006-06-01
[QUOTE=moo-cow]What is the most elegant way to make Ubuntu automatically connect via DHCP on startup?
[/QUOTE]My opinion only: an rc script (launched via init.d?)

---

### Post by moo-cow on 2006-06-13
OK, looks like I've got to hit the tutorials to find out how to do this ;)
Thx for the tip!

---

