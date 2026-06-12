---
title: "Cannot connect to internet"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by warren010 on 2010-03-27
Cannot connect to internet on newly installed Ubuntu. The wireless connection shows that it is connected with good signal strength. Firefox will not connect.

---

### Post by Iowan on 2010-03-27
Presumably, **ifconfig -a** should show an IP address. Can you **ping** the router? If so, check **route -n** to verify that the machine uses the router for it's default gateway.

---

