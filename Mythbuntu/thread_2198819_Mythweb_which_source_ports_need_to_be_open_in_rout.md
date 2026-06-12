---
title: "Mythweb which source ports need to be open in router firewall"
date: 2014-01-10
forum: Mythbuntu
---

### Post by jabrown65 on 2014-01-10
In order to get MythWeb working I have had to do the following in my Billion 7402NX Router:

Port Forward: ports 8080-8080 to the internal IP address of the MythTV machine
Firewall packet filter: 
   TCP
   destination port 8080~8080
   source port 0~65535
   inbound Allow
   outbound Allow

Having the source port wide open like that is surely unnecessary.

What source port/s do I need to open for MythWeb?

John

---

### Post by tomearp on 2014-01-10
If the remote connection you are using to access your MythWeb front end is using [NAT]("http://www.openbsd.org/faq/pf/nat.html#works") (extremely likely), or another address translation technique, then the source port as seen by your router's firewall could be pretty much anywhere in the range 1025-65535.

If you are concerned about security then I assume you have read [the wiki]("http://www.mythtv.org/wiki/MythWeb") and implemented an authentication technique?
Personally, I would prefer not to expose it directly to the Internet; use of SSH tunnelling, or L2TP/IPsec VPN, would be preferable to me.

---

