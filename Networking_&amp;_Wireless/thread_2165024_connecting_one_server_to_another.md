---
title: "connecting one server to another"
date: 2013-08-02
forum: Networking &amp; Wireless
---

### Post by zaine2 on 2013-08-02
im trying to connect one of my servers to another one through ethernet. i have 2 network cards in my first server. eth0 is connected to my router and eth1 is connected to my other ubuntu server. im not sure how to set up what configurations so that my 2nd server has internet access.

---

### Post by ian-weisser on 2013-08-03
Connecting your second server directly to the router is generally easier...and more maintainable.

If you really need the to connect through the first server NIC, then see [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) for how to do it.

---

### Post by newbie-user on 2013-08-03
Assuming your servers' network cards can auto-switch between straight-through and cross-over cables, all you would need to do is set up a static ip on the second server with the first server as the default gateway for the second. Don't forget to enable ip forwarding on the first server, also set masquerading in the first server's iptables.

---

### Post by TheFu on 2013-08-03
Normally computers are connected to a router in a "star" layout.  If you outgrow the number of switch ports on the router, then a cheap switch can be connected to 1 router port and the remaining switch ports will act like an extension of the router. No added configuration necessary.

---

