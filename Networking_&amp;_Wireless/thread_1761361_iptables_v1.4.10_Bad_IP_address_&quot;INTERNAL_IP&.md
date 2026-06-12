---
title: "iptables v1.4.10: Bad IP address &quot;INTERNAL_IP&quot;"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by FernandoTertiary on 2011-05-18
Hola,

Am configuring OpenSim for a Robust GridServer & am getting an error when attempting to run the command: 
```
iptables -t nat -A OUTPUT --dst ***EXTERNAL_IP*** -p tcp --dport 9000:9010 -j DNAT --to-destination **INTERNAL_IP**
```
...the return effect is the error
> iptables v1.4.10: Bad IP address "INTERNAL_IP"

Please help por favor.
Gracias,

---

