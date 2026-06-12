---
title: "route traffic  ip  through specific  interface"
date: 2012-02-05
forum: Networking &amp; Wireless
---

### Post by leonbravo on 2012-02-05
This is the intelectual challenge for some of you with amazing abilities in networking from an ubuntu machine....

I use a laptop (specifications not very important) and I  connect to internet through two interfaces: wlan, and wireless modem (ppp0). 

Some of the rules associated with the wlan are to denied the access to social networks.... so I tried to bound all connections to that social network through the ppp0 interface.

I run dig to find out a bunch of different ips from that social network use and add them to my iptables using 

**ip route add to *ipsocialnetwork* dev ppp0 metric 1**

What expect to see after this? all the trafic to the social network being handle by the ppp0 interface, right?

Well, firefox still getting the message from the rule in the wlan gateway. Even when I try using directly one of the IPs included previously with ip route add. 

After checking the flow of packages with wireshark I found  that in fact the packages are flowing through the wlan.....


:confused:  anyone can provide me with some insights?

---

### Post by helgman on 2012-02-06
So, you're trying to redirect traffic to specific IP addresses out a modem line while sending all other Internet bound traffic out the WLAN, is this correct?

Could you post your routing table just to give a hint about what information the router is using to make its decisions? This might help in the investigation ...

Regards,
Helgman

---

