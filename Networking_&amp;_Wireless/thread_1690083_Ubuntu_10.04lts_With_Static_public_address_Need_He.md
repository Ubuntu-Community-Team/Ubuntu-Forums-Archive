---
title: "Ubuntu 10.04lts With Static public address Need Help."
date: 2011-02-17
forum: Networking &amp; Wireless
---

### Post by hatchetheavyhaul on 2011-02-17
I been trying to get this box to connect for weeks ... 

I have static ips on the lan (win7) will connect via those But when i change over to Ubuntu 

ITs will not connect I have tried dhcp and Static ips setting in the network ... 

I even tried 192.168.1.1 and will not connect to router with that 

the only address I can get it to connect to is 192.168.0.1  


Is there a hidden setting some where in ubuntu 

Please help 

Thanks

---

### Post by dineshs on 2011-02-18
Please post the results of the following terminal commands(applications-accessories-terminal)
```
cat /etc/network/interfaces
ifconfig -a
route -n
```

---

