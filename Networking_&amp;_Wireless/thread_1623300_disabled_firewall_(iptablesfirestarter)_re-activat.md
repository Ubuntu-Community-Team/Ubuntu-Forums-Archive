---
title: "disabled firewall (iptables/firestarter) re-activates after DHCP leases"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by Kedaeus_Sendre on 2010-11-16
I'm having trouble with IPTABLES/Firestarter responding to DHCP requests.

Before installing firestarter I flushed the rules from iptables
```
iptables -F
```

and still could not get a DHCP lease from dnsmasq on a client machine. Monitoring the network via gnome-system-monitor I could see the incoming DHCP requests but the server wasn't responding to them. 

I installed firestarter so I could monitor exactly what was going on with the firewall.

I noticed that when I disable the firewall (firestarter) and restart the client computer I receive the request and the server responds with an IP.. then the firewall is re-enabled and subsequent requests (dhcp, nfs, ping) are all ignored even though there are NO rules setup in iptables or listed in firestarter.

Why on earth is this happening?

Thanks,
Kedaeus

Solution: added policy in firestarter to accept requests from address 0.0.0.0

---

