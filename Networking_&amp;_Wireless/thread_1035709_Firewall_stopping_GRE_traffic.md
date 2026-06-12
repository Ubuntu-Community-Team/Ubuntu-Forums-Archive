---
title: "Firewall stopping GRE traffic"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by Rablador on 2009-01-10
Hi!

When trying to use a VPN connection in Ubuntu, Firestarter always blocks the GRE traffic. I have tried to add new rules to iptables, but nothing helps. Any ideas for a solution?

/Jon

---

### Post by jgoguen on 2009-01-10
Did you add any new rules specifically for protocol 47?  That's GRE.  If not, you'll need something like this:
```
iptables -A INPUT -p 47 -j ACCEPT
```

---

### Post by Rablador on 2009-01-10
Hmm, doesn't seem to help... As soon as I turn off the firewall (in Firestarter) I can connect, but I do want to keep my firewall running...

---

