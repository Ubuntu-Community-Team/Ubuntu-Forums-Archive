---
title: "iptables-restore error on &quot;commit&quot;"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by cherva on 2012-02-01
I have an iptables-save generated script and it works fine. If I change the "-j DROP" to "-j REJECT --reject-with tcp-reset" I get 
```
iptables-restore: line 393 failed
``` This is the commit line....
Is there a module I have to modprobe ?

```
 modprobe -l | grep REJECT
kernel/net/ipv4/netfilter/ipt_REJECT.ko
kernel/net/ipv6/netfilter/ip6t_REJECT.ko

```

---

