---
title: "can not ping ubuntu KK machine, internet/network ON machine works"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by midaskensai on 2010-03-18
Hello,

I have an ubuntu kk laptop connected via wireless to my mixed network (xp, win7, other ubuntu), but i can not ping said machine or connect via ssh. Internet and smb-browsing ON this machine work, as does pinging FROM it. If this was a windows machine, I'd say a firewall is in the way, but since it's a vanilla karmic install, this should not be the case (or should it?).

Help?

edit: pinging the hostname resolves the ip correctly, but 100% no reply; pinging the ip yields also no reply.

---

### Post by Iowan on 2010-03-18
> **midaskensai said:**
> . If this was a windows machine, I'd say a firewall is in the way, but since it's a vanilla karmic install, this should not be the case (or should it?). You can check **iptables -L** to see if any (firewall) rules exist.

---

### Post by midaskensai on 2010-03-22
output looks like this:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
i was actually able to connect once today, but it stopped. no idea why either one happened.

---

