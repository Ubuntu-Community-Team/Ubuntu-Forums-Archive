---
title: "network-manager-pptp"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by aolong62 on 2009-01-19
8.0.4 LTS

I need to configure a pptp connection to Windows VPN. This functionality is provided by network-manager-pptp, which I have installed. The problem is that the entry for VPN only shows up in NM applet when ETH0 is set in roaming mode, the minute I assign a static by editing /etc/network/interfaces, the VPN section is not available and all I see is an option for "manual configuration".

/etc/network/interfaces::

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.10.90
network 192.168.10.0
gateway 192.168.10.1
netmask 255.255.255.0
broadcast 192.168.10.255

As I recall, I installed network-manager-pptp on another machine (also 8.0.4 LTS) and had no such problem.

Thanks,
Andrew

---

