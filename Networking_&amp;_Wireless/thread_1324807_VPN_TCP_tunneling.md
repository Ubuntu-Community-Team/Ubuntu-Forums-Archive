---
title: "VPN TCP tunneling"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by RoRoRed on 2009-11-12
hey,

is there a way to enable TCP tunneling for VPN?

---

### Post by Yoann Juet on 2009-11-14
Do you mean IPSec/ESP encapsulation over TCP ? If so, there's plethora of solutions. For instance, Cisco gateways can encapsulate such traffic over ports 10000/udp and 10000/tcp. Otherwise, you can use SSL-based VPN solutions - Openvpn is a great open source solution -. By definition, it relies on TCP protocol.

---

