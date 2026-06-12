---
title: "IP Forwarding problem (maybe)"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by Dang-er on 2006-06-10
hi, i have a gateway/router which i have just upgraded from Ubuntu 5.10 to 6.06 and the network works fine on all machines, the internet from the gateway/router works fine but the internet from the other machines on the network doesnt work. 
any ideas or nuggets of wisdom would be appreciated?

---

### Post by Dang-er on 2006-06-10
Just thought i would say i managed to fix it by editing /etc/sysctl.conf
i uncomented the line
net.ipv4.ip_forward = 1
and restarted networking and procps.sh
and now it works

---

