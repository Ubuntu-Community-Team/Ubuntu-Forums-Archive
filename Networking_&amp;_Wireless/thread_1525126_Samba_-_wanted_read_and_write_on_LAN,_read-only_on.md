---
title: "Samba - wanted: read and write on LAN, read-only on vpn.."
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by Taijitu on 2010-07-06
Hello everyone and thanks for reading this :-).

I have a samba setup of rather simple shares with ~30 users and, until now, these shares have only been accessible from LAN. We are, however, in the process of giving everyone vpn access with openvpn, but for security reasons, we don't want people to have write-access when accessing via VPN.

My idea is that the VPN-users are on 10.8..-subnet while LAN-users are on 192.168..-subnet, and that you could somehow change the rights with this, but the "hosts deny 10.8.." is not viable, as you might know.

One alternative would be to duplicate all shares, as in having one "Projects-LAN"-share and one "Projects-VPN"-share, both pointing to the same path, but with different allowances regarding hosts. This seems rather tedious, though...

If anyone has a better idea, it will be more than welcome! :-D

---

