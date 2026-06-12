---
title: "iptables Bandwidth Monitoring"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by Atomic Fusion on 2010-09-09
I have a router running OpenWRT. I'm trying to monitor monthly bandwidth usage using iptables. I did:
```

iptables -N bandwidth
iptables -A bandwidth -s 192.168.100.0/24
iptables -A bandwidth -d 192.168.100.0/24
iptables -A bandwidth -s computer.lan
iptables -A bandwidth -d computer.lan
iptables -A FORWARD -j bandwidth
```However, nothing is going into the bandwidth chain at all.
Where did I mess up?

Thanks,
Stephen

---

