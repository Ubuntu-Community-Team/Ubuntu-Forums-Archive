---
title: "Iptables port forwarding problem"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by ask2me007 on 2009-07-16
Iam using ubuntu 8.04 as router.As i tried to port forward using iptables,the function is not working.I have executed te following commands.eth1is used as external ip and eth0 is internal ip.

iptables -t nat -A PREROUTING -p tcp -i eth1 -d 192.168.0.239  --dport 8080 -j DNAT --to 192.168.10.99:8080
iptables -A FORWARD -p tcp -i eth1 -d 192.168.10.99 --dport 8080 -j ACCEPT

Pls help me to settle the problem.Iam under nat and also a firewall is running on m server.
How can i troublesoot the problem???
Thhanks in advance.

---

### Post by nixscripter on 2009-07-29
Did you enable IP forwarding in the kernel?

```
sudo bash -c 'echo 1 >/proc/sys/net/ipv4/ip_forward'
```

---

