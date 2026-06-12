---
title: "1:1 nat with iptables"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by Metallion on 2011-03-25
I've got an ubuntu host with 2 qemu virtual machines in it. They're set up bridged with a tap interface so they both have their own ip address and are accessible from the outside.

Their ips are:
```

VM1: 10.1.0.10
VM2: 10.1.0.11
Netmask for both: 255.255.255.0

```

Now I am trying to add iptables rules to the host machine to nat both virtual machines to subnet 172.16.0.0/24. I use the following rules for this.

```

iptables -P FORWARD DROP
iptables -A FORWARD -s 10.1.0.0/24 -j ACCEPT
iptables -A FORWARD -d 10.1.0.0/24 -j ACCEPT
iptables -A INPUT -s 10.1.0.0/24 -j ACCEPT
iptables -A INPUT -s 172.16.0.0/24 -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -t nat -A POSTROUTING -s 10.1.0.10 -j SNAT --to 172.16.0.10
iptables -t nat -A POSTROUTING -s 10.1.0.11 -j SNAT --to 172.16.0.11

```

The host machine has 3 interfaces.

Eth0 which is the external interface connected to the internet
Tap0 which is the tap interface for the first VM
Tap1 which is the tap interface for the second VM
These are all added to a bridge called br0 that has the external connection set up.

When I try to ping google from inside VM1, I see this going through tap0.

```

10113.790379    10.1.0.10 -> 8.8.8.8      DNS Standard query A www.google.com

10113.834219 Cisco_42:4f:60 -> Broadcast    ARP Who has 172.16.0.10?  Tell 172.16.0.1

```

And this through eth0.

```

10348.090665  172.16.0.10 -> 8.8.8.8      DNS Standard query A www.google.com

10348.134424 Cisco_42:4f:60 -> Broadcast    ARP Who has 172.16.0.10?  Tell 172.16.0.1

```

So apparently the source nat is properly happening when the dns request for google goes out but then the response doesn't know where to find 172.16.0.10.

Does anyone know how to solve this? Perhaps through virtual interfaces? If possible, I would like to handle this on the host OS without tinkering with the VM's internal network settings.

---

