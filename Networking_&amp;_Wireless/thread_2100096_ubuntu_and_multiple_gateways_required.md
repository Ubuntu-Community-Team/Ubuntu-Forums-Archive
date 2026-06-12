---
title: "ubuntu and multiple gateways *required*"
date: 2012-12-31
forum: Networking &amp; Wireless
---

### Post by briermay on 2012-12-31
having an issue with Ubuntu 12.04. my isp has given me 2 static ip address unforntunatly on separate networks with separate gateways. no matter what I have tried after adding them if I specify a gateway on each interface I get the file exists rtnetlink error. but my problem is if there isn't a gateway specified then the ip is not useable (can't access apache, ping ssh or anything to that ip)
 
what makes no since is why can I now access the ip of the machine without having a gateway assigned to it ?
 
I hate cable companies
they give you like for example
192.168.0.30 gateway is 192.168.0.29
192.168.0.34 gateway is 192.168.0.34
 
type of addressing
 
any suggestions why the ip that doesn't have its gateway set can't be accessed ?

---

### Post by Tony Flury on 2012-12-31
from what iu understand a gateway is required for you to get out from your network to the wider world. A lot depends on it your router does NAT, etc.

If something does not work - go back to your ISP.

---

### Post by sffvba[e0rt on 2012-12-31
*Thread moved to **Networking & Wireless**.*


404

---

### Post by briermay on 2012-12-31
I figured it out using iproute 2 and multiple routing tables:
```

/bin/ip route add {network 1} dev eth0 src {ip1} table wan1
/bin/ip route add default via {gateway 1} table wan1
/bin/ip route add {network 2} dev eth2 src {ip2} table wan2
/bin/ip route add default via {gateway 2} table wan2
/bin/ip rule add from {ip 1} table wan1
/bin/ip rule add from {ip 2} table wan2
/bin/ip route add default scope global nexthop via {gateway 1} dev eth0 weight 5 nexthop via {gateway 2} dev eth2 weight 5

```

---

