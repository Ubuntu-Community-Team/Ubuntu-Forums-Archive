---
title: "Pptp vps"
date: 2013-02-27
forum: Networking &amp; Wireless
---

### Post by imtiax on 2013-02-27
Hi I just installed Ubuntu 12 on my VPS

I disabled ufw firewall.

Installed PPTP using this tutorial [http://www.putdispenserhere.com/pptp-vpn-setup-guide-for-a-debian-openvz-vps/](http://www.putdispenserhere.com/pptp-vpn-setup-guide-for-a-debian-openvz-vps/)

> 
Stopping firewall and allowing everyone...
root@vpn2:~# iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
root@vpn2:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
root@vpn2:~#


How can I open all ports on my VPN? I can browse websites on the VPN fine, but all ports are closed.

I'm using this 
Ubuntu 12.04 LTS x86 Minimal

---

