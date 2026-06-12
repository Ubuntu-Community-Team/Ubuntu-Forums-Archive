---
title: "iptables: how to block incoming and allow outgoing traffci"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by asashour on 2011-01-06
Dear all,

I need to configure iptables to block incoming traffic (except specific ports), but allows all outgoing traffic.

I am able to block incoming traffic, but doing so also prevents outgoing traffic (tested by telnet [www.google.com]("http://www.google.com") 80)

The following was used:

iptables -A INPUT -p tcp --dport ssh -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -I INPUT 1 -i lo -j ACCEPT
iptables -A INPUT -j DROP


Also, even allowing NOT SYN requests still prevents outgoing traffic.

iptables -I INPUT 1 -p tcp ! --syn -j ACCEPT


Another point: 

# modinfo ipt_state
modinfo: could not open /lib/modules/2.6.18-028stab070.14/modules.dep

How to install ipt_state module on ubuntu?

Ahmed

---

### Post by JeffDavidoff on 2011-01-06
I usually use something like this to allow established connections. It uses the connection state to by-pass rule checking:

```
iptables -A INPUT  -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```

---

### Post by asashour on 2011-01-07
Thanks a lot for your help

---

