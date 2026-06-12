---
title: "iptables limit-burst, set, hit-count"
date: 2011-05-30
forum: Networking &amp; Wireless
---

### Post by Lars Noodén on 2011-05-30
I would like [iptables](http://linux.die.net/man/8/iptables) to allow only 4 new connection attempts per minute.  What part of the rules for this chain are wrong/redundant?

```

iptables -I INPUT -i ${EXT} -p tcp --destination-port 22 -j SSH;


iptables -I SSH -m limit --limit 4/minute --limit-burst 6 -j ACCEPT;

iptables -I SSH -m state --state NEW -m recent \
  --update --seconds 60 --hit-count 6 -j REJECT

iptables -I SSH -m state --state NEW -m recent --set

```

---

