---
title: "Internet connection disappeared"
date: 2012-05-20
forum: Networking &amp; Wireless
---

### Post by Shafaet on 2012-05-20
I am using pppoe connection for over 2 years. I login using pppoeconf in terminal. 
For last 2 days i couldn't connect with internet in ubuntu 10.10 or mint10 though in windows everything is fine. 

I use broadband.
 
Some info after login:
> 
//plog
May 21 00:17:24 shafaet-EP43-UD3L pppd[2093]: Connect: ppp1 <--> eth1
May 21 00:17:24 shafaet-EP43-UD3L pppd[2093]: Remote message: Login ok
May 21 00:17:24 shafaet-EP43-UD3L pppd[2093]: PAP authentication succeeded
May 21 00:17:24 shafaet-EP43-UD3L pppd[2093]: peer from calling number 00:00:00:EE:FF:F1 authorized
May 21 00:17:24 shafaet-EP43-UD3L pppd[2093]: not replacing existing default route through ppp0
May 21 00:17:24 shafaet-EP43-UD3L pppd[2093]: Cannot determine ethernet address for proxy ARP
May 21 00:17:24 shafaet-EP43-UD3L pppd[2093]: local  IP address 10.15.7.148
May 21 00:17:24 shafaet-EP43-UD3L pppd[2093]: remote IP address 10.15.0.1
May 21 00:17:24 shafaet-EP43-UD3L pppd[2093]: primary   DNS address 10.15.0.10
May 21 00:17:24 shafaet-EP43-UD3L pppd[2093]: secondary DNS address 10.15.0.11

//more info
Network device:    eth1
Hardware address:    00:11:3b:17:ec:74
Multicast:    Enabled
MTU:    1500
Link speed:    not available
State:    Active
Transmitted packets:    130
Transmission errors:    0
Received packets:    249
Reception errors:    0
Collisions:    0



Please help me if you can.

Edit:
Ok i've solved the problem. The dns screwed somehow,i could access the internet by directly typing the ip of sites. Than i changed the dns in /etc/resolv.conf file.

---

