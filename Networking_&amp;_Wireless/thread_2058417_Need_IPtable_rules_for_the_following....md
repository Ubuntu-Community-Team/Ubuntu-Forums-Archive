---
title: "Need IPtable rules for the following..."
date: 2012-09-15
forum: Networking &amp; Wireless
---

### Post by sefs on 2012-09-15
Hi all I have a OpenVPN server installed in bridged mode.

1/
When Clients connect I want them to not see the LAN at xxx.xxx.xxx.0/24 but only the VPN server at xxx.xxx.xxx.www which they will use for internet access.

2/
Additionally I have ssh and a webserver running on the OpenVPN Server, and would like to block these two ports from being accessed by the vpn clients which have a dhcp range of xxx.xxx.xxx.yyy - xxx.xxx.xxx.zzz.

Can someone tell me how to achieve this with some simple and concise rulesets.

Thanks.

---

### Post by sefs on 2012-09-15
```

iptables -A INPUT -p udp --dport 1194 -j ACCEPT
iptables -A INPUT -p tcp -m iprange --src-range 172.25.26.90-172.25.26.99 --dport 22 -j DROP
iptables -A INPUT -p tcp -m iprange --src-range 172.25.26.90-172.25.26.99 --dport 80 -j DROP
iptables -A INPUT -i tap0 -j ACCEPT 

iptables -A FORWARD --dst 172.25.26.252 -j ACCEPT 
iptables -A FORWARD -m iprange --src-range 172.25.26.90-172.25.26.99 --dst 172.25.26.0/24 -j DROP 
iptables -A FORWARD --src 172.25.26.0/24 -m iprange --dst-range 172.25.26.90-172.25.26.99 -j DROP 

```

Do the above rules look like they would accomplish what I need?

---

