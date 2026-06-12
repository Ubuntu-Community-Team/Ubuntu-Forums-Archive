---
title: "Using Ubuntu to route over vpn"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by tororm on 2009-07-14
Hi, 


I have had a good look around and cannot find any information on this. 

My Task:

I have 2 remote locations that I connect to over open VPN.


I would like to connect to both OpenVpn connections on an ubuntu box (10.1.1.88) and use the ubuntu box as a router ie-

scenario 1)

request recieved to IP address A- sent over VPN 1


scenario 2)

request recieved to IP address B- sent over VPN 2


scenario 3)

request recieved to any IP that is not A or B - sent over standard internet router (10.1.1.1)

The ubuntu box I will be using only has one NIC (a virtualised machine)


Any help will be appreicated!

---

### Post by superprash2003 on 2009-07-15
im not sure if this would help [http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

