---
title: "auto detecting internet ip for iptables firewall rule?"
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by gareth40 on 2011-09-26
here is my setup:
 
InternetIP---ADSL Modem---192.168.1.0/24---WifiHotspot Router---192.168.182.1/24
 
InternetIP is dynamic
ADSL Modem internal ip 192.168.1.1
Hotspot router eth0 192.168.1.220
Hotspot router eth1 192.168.182.1
eth1 is sending out dhcp
 
I have already used iptables to block access to all known lan subnets using the following:
 
iptables -t nat -I PREROUTING -i eth1 -d 192.168.0.0/16 -j DROP
iptables -t nat -I PREROUTING -i eth1 -d 169.254.0.0/16 -j DROP
iptables -t nat -I PREROUTING -i eth1 -d 172.16.0.0/12 -j DROP
iptables -t nat -I PREROUTING -i eth1 -d 10.0.0.0/8 -j DROP
iptables -t nat -I PREROUTING -i eth1 -d 192.168.182.1/32 -j ACCEPT
 
That all works fine. However I would also like to add the InternetIP to that list aswell, easy to do if the InternetIP is static, however if its dynamic is there a detection command to use instead?
 
I want to use the following rule:
iptables -t nat -I PREROUTING -i eth1 -d InternetIP/32 -j DROP 
and I need to somehow automatically detect the Internet IP and insert it into the iptables rule.
 
The reason for this, it stops wifi hotspot users going to [www.showip.com]("http://www.showip.com"), finding out what the Internet IP is and then trying to connect to it using http:// in the address bar. This will often bring up the admin web page (if one exists) of the ADSL/Cable modem or Internet NAT router, even if its not enabled on the Internet side of the router.

---

