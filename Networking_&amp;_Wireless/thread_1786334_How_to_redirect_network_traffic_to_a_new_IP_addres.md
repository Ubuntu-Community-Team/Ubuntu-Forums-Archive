---
title: "How to redirect network traffic to a new IP address using IPtables"
date: 2011-06-19
forum: Networking &amp; Wireless
---

### Post by coader on 2011-06-19
Hai,

I am new in networking field. Can any one please tell me how to redirect network traffic to a new IP address using IPtables. I am using Baffalo router and the rtos used is DD-WRT.

Basically, I want it so that any connection going  through  my router to a specific IP (say, 192.168.11.5) will be  redirected to another IP (say, 192.168.11.7) so any outgoing connections made  by a program that is attempting to connect to192.168.11.5 will instead  connect to 192.168.11.7.Any help would be appreciated:)

---

### Post by poolet on 2011-06-19
enable ip forwarding::

```

echo "1" /proc/sys/net/ipv4/ip_forward
if not works try::
sysctl net.ipv4.ip_forward=1

```add a rule telling to forward the traffic to specific port::
```

iptables -t nat -A PREROUTING -p tcp --dport 1111 -j DNAT --to-destination 2.2.2.2:1111

```ask IPtables to masquerade: 

```

iptables -t nat -A POSTROUTING -j MASQUERADE

```you could redirect the traffic from a specific network with, for a host only:

```

# iptables -t nat -A PREROUTING -s 192.168.1.1 -p tcp --dport 1111 -j DNAT --to-destination 2.2.2.2:1111

```or for the whole network:: 
```

iptables -t nat -A PREROUTING -s 192.168.1.0/24 -p tcp --dport 1111 -j DNAT --to-destination 2.2.2.2:1111

```


Hope to help you

---

### Post by smaon on 2011-07-04
Hi,

thank you, this information has been very useful for me in a similar configuration. A strange thing is that download speed is reaaaaallly slow now from the outside. Network bandwidth is > 1MB/s and I download form the internal server at about 10KB/s. 

Is this normal to have such an impact with IP forwarding? I don't see why it should be...

Thanks,

Smaon

---

