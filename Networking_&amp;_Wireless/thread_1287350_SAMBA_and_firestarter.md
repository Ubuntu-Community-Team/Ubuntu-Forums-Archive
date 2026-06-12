---
title: "SAMBA and firestarter"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by enoughsaid05 on 2009-10-10
Hi there

I just finally got my ubuntu box to function as samba file server on my windows network. But I can do so only after when I get my firestarter to disable the firewall. When I close the firestarter, I wouldn't be able to share files again.

How do I get my firestarter to allow samba to share files?

many thanks

---

### Post by sloggerkhan on 2009-10-10
You need to make exceptions for the port samba uses on the local side of the network.

It can be done easily in firestarter gui.

---

### Post by enoughsaid05 on 2009-10-10
How do I get to do that? I tried making a few exceptions, allowing incoming connections for local IP, allow ports and so on. But I can't sign into my ubuntu box from vista.

---

### Post by sloggerkhan on 2009-10-10
[http://www.fs-security.com/docs/policy-page.php](http://www.fs-security.com/docs/policy-page.php)

---

