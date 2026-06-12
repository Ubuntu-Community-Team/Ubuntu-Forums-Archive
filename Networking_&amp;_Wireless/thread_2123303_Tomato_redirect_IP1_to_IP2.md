---
title: "Tomato: redirect IP1 to IP2"
date: 2013-03-07
forum: Networking &amp; Wireless
---

### Post by R33D3M33R on 2013-03-07
Hello,

I would like to setup my WRT54GL that has Tomato installed so it could redirect IP1 requests to IP2. Both IP1 and IP2 are external IPs. There is currently no way to set this redirect on the problematic machine, so I would force this with my router. 

Thanks in advance for any working redirecting example script!

---

### Post by R33D3M33R on 2013-03-11
I have tried to add this to scripts/Firewall:

```
iptables -t nat -A PREROUTING -d IP1 -j DNAT --to-destination IP2
iptables -t nat -A POSTROUTING -j MASQUERADE
```

But it doesn't work at all. Since IP1 is offline, a ping to IP1 should work only if this rule is working, but it there is no response from the server. What could I be doing wrong?

/edit: it actually does work, but you have to reboot the router, not just save the command.

---

