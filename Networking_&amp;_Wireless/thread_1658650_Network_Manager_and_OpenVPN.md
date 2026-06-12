---
title: "Network Manager and OpenVPN"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by roton on 2011-01-02
When I try to connect to a VPN through Network Manager it connects fine and I get the padlock icon but cannot access the Internet - it just times out.
However, when I use terminal and type "openvpn /etc/var/openvpn/openvpn.conf" it connects fine and everything works!

Both are using the same openvpn.conf so why is terminal working fine but Network Manager not? :(

What am I missing?

---

### Post by roton on 2011-01-10
Bump.

---

### Post by Xanthomryr on 2011-01-15
Edit your VPN connection in network-manager, go to IPv4 settings -> Routes and then activate "Use this connection only for resources on its network".

---

### Post by roton on 2011-01-16
> **Xanthomryr said:**
> Edit your VPN connection in network-manager, go to IPv4 settings -> Routes and then activate "Use this connection only for resources on its network".

Thanks for the reply. When I tick that box it connects to the vpn but uses my own connection for web surfing etc so it's not actually using the vpn connection for everything.
Any other ideas?

---

