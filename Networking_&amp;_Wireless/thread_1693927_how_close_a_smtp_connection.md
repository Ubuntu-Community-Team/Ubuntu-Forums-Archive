---
title: "how close a smtp connection?"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by mihafan on 2011-02-23
Every time we turn on the computer automatically opens a TCP connection to a local mail server host-static-93-116: smtp "server receives this message, it is one which I have recently installed program is called Koha. (Koha ILS is an integrated library system)
How can I stop this?
I attached the output of netstat in file f123.txt

---

### Post by SeijiSensei on 2011-02-24
1) Add a firewall rule on the box that blocks output to that address:

```
iptables -A OUTPUT -j REJECT -d address.of.remote.server
```

2) Perhaps you should figure out why the application is sending this message?  Is it checking in with the software's publisher?  Is there a configuration setting you can change to disable the emails?

---

### Post by SeijiSensei on 2011-02-24
You marked this thread Solved without telling us what worked for you.

---

