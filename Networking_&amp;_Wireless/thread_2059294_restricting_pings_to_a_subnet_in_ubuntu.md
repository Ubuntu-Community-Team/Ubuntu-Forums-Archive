---
title: "restricting pings to a subnet in ubuntu"
date: 2012-09-17
forum: Networking &amp; Wireless
---

### Post by sefs on 2012-09-17
Hi there,

Windows 7/vista has a default firewall profile such that if I ping a win7 machine from a subnet other than the one the win7 machine is on win7 will not respond.

I tried this with ubuntu and ubuntu replies to pings from hosts on other subnets that ubuntu is not present on.

I want to set up the ubuntu like the win7 host in respect to this.

I could probably use iptables and do this...

```

iptables -A INPUT -p icmp --icmp-type echo-request ! --src 192.168.1.0/24 -j  DROP

```

... but is there a gui way to do it via gufw? or even with ufw at the cli without fiddling with iptables?

---

