---
title: "NM and user routes problem"
date: 2013-05-04
forum: Networking &amp; Wireless
---

### Post by kapetr on 2013-05-04
Hello,

for security reason I use locked DNS setting (chattr +i /etc/resolv.conf).
Sometimes I use VPN services, but they in common do not allow other then own DNS servers.
So I need to add route to my DNS servers via "previous" default GW (eth0 or ppp0).

To do so manually is no problem but how to do so automatically in NetworkManager ?
If I use "routes" in NM applet then the "new" == (over VPN - ppp0/1) gateway is used, not "previous" default GW.

I would like to use own script in  /etc/NetworkManager/dispatcher.d/, but problem is (see man NetworkManager), that it seems there are no script params/variables filled with "previous" default GW.

FYI - I use many ADSL routers, ... with many LAN IP ranges, ... => I do not know IP addres of "previous" def. GW. It is sometimes 192.168.2.1, 192.168.1.200, 10.0.0.138, .... and sometimes it is public address if PPPoE is used, ... 

Any Idea ?

P.S.: Sorry please my English.

---

