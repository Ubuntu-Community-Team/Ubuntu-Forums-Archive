---
title: "Squid transparent proxy on multiple networks"
date: 2012-05-21
forum: Networking &amp; Wireless
---

### Post by Chrus on 2012-05-21
Having a bit of trouble getting my squid setup working.

Im setting up a router with 2 networks, 1 for staff (172.30.40.0 - br0) and 1 for guests (172.30.44.0 - br0.10). I need squid to act as a transparent proxy on both networks with different rules in squid and iptables to say what each network has access to.

Fromt he staff network, everything works properly. The guest network is having a few issues tho. Cant load webpages from the guest network. Infact theres nothing in the squid logs about the guest net even trying to access websites. However, if i manually set my browser to use the proxy (IP and port), squid works brilliantly. So from that, I've narrowed the problem down to my firewall rule.

```

INTERNAL_IP=172.30.40.1/32
INTERNAL_NET=172.30.40.0/24
INTERNAL_IF=br0

GUEST_IP=172.30.44.1/32
GUEST_NET=172.30.44.0/24
GUEST_IF=br0.10

$IPTABLES -t nat -A PREROUTING -i $INTERNAL_IF -d ! $INTERNAL_NET -p tcp --dport 80 -j REDIRECT --to-port 3128
$IPTABLES -t nat -A PREROUTING -i $GUEST_IF -p tcp --dport 80 -j REDIRECT --to-port 3128
```

Now I've had this working before in a similar setup, the only difference being last time I didnt have the bridge or vlan happening, it was just a 'new' network plugged into eth1 and an 'old' network plugged into eth2.

Am I missing something blindingly obvious? Or do I need to do things differently to get them to work with bridges/vlans?

Thanks

---

### Post by Chrus on 2012-05-21
Bump!

---

### Post by Chrus on 2012-05-22
Anyone? Anything?

---

### Post by Chrus on 2012-05-23
One more bump

---

