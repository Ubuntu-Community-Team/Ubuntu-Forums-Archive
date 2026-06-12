---
title: "help me! i want to setting proxy in ubuntu server"
date: 2012-05-09
forum: Networking &amp; Wireless
---

### Post by kitten257 on 2012-05-09
My lab have 3 pc
1: Proxy server setup squid
IP Card 1 connect to internet: 192.168.1.2/24, gateway: 192.168.1.1
IP Card 2 connect to LAN: 10.10.30.1/24

2: ubuntu server
IP Card 1 in LAN connect to Card 2 of proxy server: 10.10.30.2/24, gateway: 10.10.30.1, domain name 8.8.8.8
and i modify file
- vi /etc/profile
- vi /etc/environment 
- vi /etc/bash.bashrc
add
export http_proxy=http://10.10.30.12:8888
but ubuntu server can't connect to internet

i setup ubuntu server version 10.4
i can't see file apt.conf

3: PC XP in LAN:  10.10.30.3/24, gateway 10.10.30.1
i configure proxy for IE and connect to internet => ok

please hep me! thank all!

---

