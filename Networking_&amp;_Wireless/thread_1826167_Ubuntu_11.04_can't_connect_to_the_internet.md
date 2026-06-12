---
title: "Ubuntu 11.04 can't connect to the internet"
date: 2011-08-16
forum: Networking &amp; Wireless
---

### Post by cityoftroy on 2011-08-16
Hi, I have an Hp a250n desktop (yes, very old) and I just installed 11.04 on it and it has not been able to connect to the internet through a wired ethernet connection.  I've installed Ubuntu before on this machine and it never had a problem connecting.  any ideas on what could be the problem?

---

### Post by praseodym on 2011-08-21
Hello,

what hardware do you use? Please show the following terminal outputs:

```
lspci -nnk | grep -iA2 net
lsmod
cat /etc/network/interfaces
```

---

