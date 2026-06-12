---
title: "How to open port for BT downloads using Transmission"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by H3R3T1K on 2010-10-19
Transmission says my port is closed. If I google the problem, it just gives me advice on how to open a port in Windows OS. There's no firewall in Ubuntu 10.10 by default, right? There isn't any router used neither. I'm living in a dorm. I just plug the LAN cable in the box fixed to the wall. Hope you guys can help me out.

Cheers

---

### Post by Barriehie on 2010-10-19
You have to open the port via iptables.  As root, the command will look something like:
```

iptables -A INPUT -p ***protocol*** --dport ***port#*** -j ACCEPT
```

You can find a primer on iptables [here](http://bodhizazen.net/Tutorials/iptables/).

HTH

---

### Post by Grenage on 2010-10-19
> **H3R3T1K said:**
> Transmission says my port is closed. If I google the problem, it just gives me advice on how to open a port in Windows OS. There's no firewall in Ubuntu 10.10 by default, right? There isn't any router used neither. I'm living in a dorm. I just plug the LAN cable in the box fixed to the wall. Hope you guys can help me out.

Cheers

I would imagine that it's being blocked by the campus gateway.  Most academic institutes don't want their network becoming a torrent farm.

---

### Post by MechaMechanism on 2010-10-19
> **Grenage said:**
> I would imagine that it's being blocked by the campus gateway.  Most academic institutes don't want their network becoming a torrent farm.
Thats too bad, because it means we can't help him.  I think the COC forbids help in trying to get around firewalls, like say China, corporate, campus.

---

