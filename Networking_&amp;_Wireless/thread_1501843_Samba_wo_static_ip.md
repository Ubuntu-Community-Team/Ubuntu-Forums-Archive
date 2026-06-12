---
title: "Samba w/o static ip"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by SOG420 on 2010-06-04
I've read a few tutorials on samba and they all include instructions that include a mandatory static ip for samba. Is there a way to have a dynamic ip?
Thanks

---

### Post by bab1 on 2010-06-04
> **SOG420 said:**
> I've read a few tutorials on samba and they all include instructions that include a mandatory static ip for samba. Is there a way to have a dynamic ip?
Thanks

How would you find the server unless you knew its IP address?  There are other side effects to using DHCP too.  Every time the DHCP lease is renewed the Samba daemon will reload.

---

