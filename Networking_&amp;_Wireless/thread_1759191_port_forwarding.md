---
title: "port forwarding"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by StaticPhilly on 2011-05-15
hi all,

ok heres what i want to do,
basiclly i have two servers,
say 0.0.0.1 and 0.0.0.2 just for this example

now what i want is 0.0.0.1 to be like a firewall, basiclly any requests on say port 80 to forward to 0.0.0.2
both servers are allocated public static ip;s  and are not on the same router.

can anyone tell me the best way to go about this

cheers,
Phil

---

### Post by StaticPhilly on 2011-05-15
ok i worked it out

basiclly on 0.0.0.1 i set iptables up by the following:
```
echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -P INPUT ACCEPT 
iptables -P OUTPUT ACCEPT 
iptables -P FORWARD ACCEPT 
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
iptables -A FORWARD -i eth0 -j ACCEPT  
iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 80 -j DNAT --to 0.0.0.2
iptables -A FORWARD -p tcp -i eth0 -d 0.0.0.2 --dport 80 -j ACCEPT
```[B]

eth0 is the ethernet card on 0.0.0.1 so any requests to port 80 to 0.0.0.1 automatically go to 0.0.0.2 :)
[/B]

---

