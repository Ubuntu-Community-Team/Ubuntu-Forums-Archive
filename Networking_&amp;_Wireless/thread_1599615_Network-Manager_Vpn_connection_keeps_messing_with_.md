---
title: "Network-Manager Vpn connection keeps messing with the custom Dns settings?"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by kartal on 2010-10-18
Hi

I am using NM to connect to lan-internet and VPN connections. Everything works great except that NM keeps adding a DNS server IP adress related to the VPN connection to the /etc/resolv.conf which renders my internet connection useless. Basically if I drop the VPN connection I get my internet back. The internet works for certain sites and does not work for some others when I have the VPN enabled. 


How can I stop NM from editing the /etc/resolv.conf file so that I the system only uses a single DNS server I have defined in the Lan connection(manual Dns server)? 



thanks

---

