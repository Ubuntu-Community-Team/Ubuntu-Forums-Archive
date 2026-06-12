---
title: "Linux Nat Netfilter"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by macrig on 2010-03-10
Hi to all,
I'm working to modify linux nat system, exactly assignment port procedure.
In order to make the change i'm modifying the nf_nat_proto_common.c source file and bool nf_nat_proto_unique_tuple(.....) function. This file is inside net/ipv4/netfilter.  It is correct to modify this part of the module or the assignment is provided in other file?

This is my script to configure the nat.

```
#!/bin/sh

PATH=/usr/sbin:/sbin:/bin:/usr/bin

#delete all existing rules
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

#Always accept loopback traffic
iptables -A INPUT -i lo -j ACCEPT

#Allow established connections, and those not coming from outside
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state NEW -i ! eth0 -j ACCEPT
iptables -A FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT

#Allow outgoing connections from the LAN side
iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT

#Masquerade
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE


iptables -A FORWARD -i eth0 -o eth0 -j ACCEPT

#Enable routing
echo 1 > /proc/sys/net/ipv4/ip_forward
```

I'm proceeding in the correct way?

Thanks to all.

Giuseppe

---

### Post by koszta on 2010-03-10
I dont honeslty understand what are you trying to do. Maybe I am just dumb but do you 
a) want to configure nat on linux?
b) are doing some development around nat on linux?

Which is it? :) In case of a) then any talk about those functions in completely unnecessary. If b) then I dont really need to see the script much but only mostly your source files and the changes you made to the originals... I guess it is a) tho... Or maybe I am just too dumb to understand you... Will be glad to help if I can. I have dealt with iptables very extensively and could call myself a little self-taught expert on those.

---

### Post by macrig on 2010-03-10
I'm going to make some development around linux nat system. I don't know if my script calls nf_nat module, and I would like to know which source code file contains the port assignment procedure.
I changed nf_nat_proto_common.c inserting some printk but that does not work.
Can you suggest me anything?

Giuseppe

---

