---
title: "Can't connect to server from internan network on externel ip"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by cherva on 2011-02-01
I have an ubuntu server 10.04 with external ip = X witch has a DHCP server and internet connection sharing to an internal network. The problem is this:
The ubuntu server forwards some ports from external to one machine on the internal netork. If I am outside (outside of the internal network) nmap shows the ports as opened and everything works. BUT if I am on the internal network and try to access these ports directly to the machine on the internal network it works, but if I type the external ip of the server that is forwarding the ports to the other machine I can't connect...
```
XXXX@XXXXXX:/home/XXXX# iptables -L -t nat -n
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
DNAT       tcp  --  0.0.0.0/0            xxx.xxx.xxx.xxx      tcp dpt:xxx to:10.10.0.201:xxx
DNAT       tcp  --  0.0.0.0/0            xxx.xxx.xxx.xxx      tcp dpt:xxx to:10.10.0.201:xxx
DNAT       tcp  --  0.0.0.0/0            xxx.xxx.xxx.xxx      tcp dpt:xxx to:10.10.0.201:xxx
DNAT       tcp  --  0.0.0.0/0            xxx.xxx.xxx.xxx      tcp dpt:xxx to:10.10.0.201:xxx

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
MASQUERADE  all  --  0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

---

### Post by cherva on 2011-02-10
Bump

---

