---
title: "Skype and iptables"
date: 2012-01-11
forum: Networking &amp; Wireless
---

### Post by Frozen Forest on 2012-01-11
I would like to get Skype working with iptables, it's possible to define port for incoming calls but not the same don't be the case for outgoing. Since iptables drop outgoing, incoming, forwarding by default does this cause some problem with skype, is there a way around it without setting policy for outgoing to accept. 

```

# SKYPE CHAIN
iptables -N skype
iptables -A skype -p udp --dport $SKYPE_PORT_IN -j accept-in
iptables -A skype -p udp --sport $SKYPE_PORT_IN -j accept-out

iptables -A INPUT -p udp --dport $SKYPE_PORT_IN -j skype
iptables -A OUTPUT -p udp --sport $SKYPE_PORT_IN -j skype

```

---

