---
title: "Specifying IP Address Range in ACL in SQUID Proxy"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by linuxrockers on 2010-02-24
I need to create two  Access Control Lists for my networks using SQUID proxy. The ip address range from 165.165.42.10 to 165.165.42.50 for one network and from 165.165.42.60 to 165.165.42.90 for another network. How can I make it?

---

### Post by gmargo on 2010-02-26
What have you tried? It's spelled out clearly in the squid.conf file.
```

#       acl aclname src      addr1-addr2/netmask ... (range of addresses)

```

---

### Post by linuxrockers on 2010-02-27
Its showing some error with my subnet mask....

---

