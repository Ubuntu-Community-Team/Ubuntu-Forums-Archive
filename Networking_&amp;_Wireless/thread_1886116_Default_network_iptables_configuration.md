---
title: "Default network iptables configuration"
date: 2011-11-24
forum: Networking &amp; Wireless
---

### Post by speedy18us on 2011-11-24
I would like to know what's the default network iptables configuration for Ubuntu server ... I don't use a firewall, but i'm planning to do so and i want to know what's the default network iptables configuration. Something in one example like this:

```
iptables -P FORWARD ACCEPT
iptables -P INPUT   ACCEPT
iptables -P OUTPUT  ACCEPT
```Thanks

---

### Post by Dangertux on 2011-11-24
> **speedy18us said:**
> I would like to know what's the default network iptables configuration for Ubuntu server ... I don't use a firewall, but i'm planning to do so and i want to know what's the default network iptables configuration. Something in one example like this:

```
iptables -P FORWARD ACCEPT
iptables -P INPUT   ACCEPT
iptables -P OUTPUT  ACCEPT
```Thanks

That's the default configuration. 

This might help : [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

---

### Post by speedy18us on 2011-11-24
I like your iptables.sh script and I would like to use it. I'll use my machine as ics and have some services, so I'm assuming that the policy **iptables -P FORWARD DROP** should be **iptables -P FORWARD ALLOW**. And the rest stays the same?

---

### Post by Dangertux on 2011-11-24
> **speedy18us said:**
> I like your iptables.sh script and I would like to use it. I'll use my machine as ics and have some services, so I'm assuming that the policy **iptables -P FORWARD DROP** should be **iptables -P FORWARD ALLOW**. And the rest stays the same?


That's not particularly designed for a NAT gateway, and some changes would have to be made. In order to achieve the NAT routing you would have to use a script more like this. You could if you want then fine tune it for what ports you want forwarded etc, however this would give you basic ICS 

```

#!/bin/bash
#Simple NAT iptables script
#
#
echo "1" > /proc/sys/net/ipv4/ip_forward
iptables --flush
iptables --table nat --flush
iptables --delete-chain
#
#
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m conntrack --ctstate NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -i eth1 -j ACCEPT

```

where eth0 is your external interface and eth1 is your internal interface.
Hope that helps.

---

