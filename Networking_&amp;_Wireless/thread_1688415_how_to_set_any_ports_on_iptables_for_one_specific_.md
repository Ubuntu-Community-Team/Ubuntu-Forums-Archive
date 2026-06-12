---
title: "how to set any ports on iptables for one specific host only?"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by remy06 on 2011-02-15
Hi,

I like to set in iptables to allow access from one host to my server on any ports.

Currently the iptables have been configured to deny all and to allow access only to those I've specified.

Can anyone advice on the command to achieve this?

---

### Post by remy06 on 2011-02-16
any ideas?

---

### Post by gmargo on 2011-02-16
What are you using for a firewall tool?

For **ufw(8 )**:
```

$ sudo ufw allow in from 192.168.1.15

```For **iptables(8 )** directly:
```

$ sudo iptables -A INPUT -s 192.168.1.15 -j ACCEPT

```

---

