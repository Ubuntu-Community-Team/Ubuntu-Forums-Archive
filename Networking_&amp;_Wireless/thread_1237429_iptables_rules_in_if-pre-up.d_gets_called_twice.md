---
title: "iptables rules in if-pre-up.d gets called twice"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by yangres on 2009-08-11
Hi:

I'm trying to place a iptables script in /etc/network/if-pre-up.d. It seems like the iptable rules get posted twice. Any ideas? This is Ubuntu 9.04 server edition that I'm using.

Neopyhte

---

### Post by Brandon Williams on 2009-08-11
Your script will be run for each interface, including loopback. The standard thing to do is to put this line at the top of the script so that it isn't run for loopback:
```
[ "$IFACE" != "lo" ] || exit 0
```

If you have more than one "real" interface, you would need to come up with some other way to ensure your script only gets run for one of the interfaces. Something similar to the above would probably work if the iptables rules only apply to one of the interfaces.

---

