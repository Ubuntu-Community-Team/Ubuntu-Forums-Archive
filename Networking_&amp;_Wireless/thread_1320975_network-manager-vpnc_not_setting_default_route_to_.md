---
title: "network-manager-vpnc not setting default route to tun0"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by kino71 on 2009-11-09
Hello,
I'm using Ubuntu 9.10, I've installed network-manager-vpnc and I can connect to my work vpn.
Every time I connect I need to run the following:

sudo ip route del default
sudo ip route add default dev tun0

to have everything working.

and in syslog I found:

Nov  9 22:40:13 franco-laptop NetworkManager: <info>  Policy set 'Auto kinopoli' (wlan0) as default for routing and DNS.

How do I get NetworkManager to use tun0 as default for routing ?

Thanks
Franco

---

### Post by kino71 on 2009-11-10
I solved this by unticking "use this connection only for resources on its network" in Network Connections -> VPN -> edit -> Ipv4 settings tab -> Routes.

cheers
Franco

---

### Post by berni_j on 2010-01-09
Thank you for posting your solution, which helped me solve the same issue.
Have a nice day,
Berni

---

### Post by rexb on 2012-10-16
+1 Thank you as well.

---

