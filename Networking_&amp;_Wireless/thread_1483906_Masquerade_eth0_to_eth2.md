---
title: "Masquerade eth0 to eth2?"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by rootk1t on 2010-05-15
Hello,

I've got 3 interfaces: eth0/1/2
eth0 = Internet
eth1 = DMZ (already routed by ISP, MASQUERADE does bad)
eth2 = LAN

I'd like to make Internet available for eth2 only, not for eth1 also. Is that possible?

I mean, what I wanna do is masquerade a specific interface only.

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
MASQUERADE  all  --  0.0.0.0/0            0.0.0.0/0

, but I'd like to exclude eth1 from MASQUERADE.

Thanks a lot!

---

### Post by rootk1t on 2010-05-17
Thanks for your support :P

I did:

iptables -A POSTROUTING -s $SUBNET -o eth0 -j MASQUERADE

where:

$SUBNET is the internal subnet
eth0 is my WAN interface


Example:

iptables -A POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE

Note: 192.168.1.0/24 is my subnet, you might need to change it regarding your needs.

---

