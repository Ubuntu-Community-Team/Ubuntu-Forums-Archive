---
title: "VPN problems sending data"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by estebe on 2009-02-20
After upgrade to Ubuntu 8.10 i've problems to connect to internet. When in fact I can connect and surf internet normaly and download my mail without problems but i can not send any mail or data on internet, even this message i must send it with windows...! I connect to internet with a VPN connection. The old config that i used was as follow


[main]
Description=Internet
Connection-Type=pptp
PPTP-Server=bi.despega.euskaltel.es
Use-Peer-DNS=yes
Encrypt-MPPE=no
Encrypt-MPPE-128=no
Compress-MPPC=no
Compress-Deflate=no
Compress-BSD=no
PPP-Lock=no
Auth-Peer=no
Refuse-EAP=yes
Refuse-CHAP=no
Refuse-MSCHAP=yes
MTU=1416
MRU=1416
LCP-Echo-Failure=10
LCP-Echo-Interval=10
PPP-Custom-Options=
Peer-DNS-Over-Tunnel=no
X-NM-Routes=
Use-Routes=no


Now in 8.10 i can not set all this parameters, like MTU and MRU. What can i do?

---

