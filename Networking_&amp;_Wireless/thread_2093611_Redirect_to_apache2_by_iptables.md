---
title: "Redirect to apache2 by iptables"
date: 2012-12-11
forum: Networking &amp; Wireless
---

### Post by apoc4l1pt0 on 2012-12-11
hi,
i have a problem, i create an access point with Internet sharing. this is work fine. i try connect with another pc and i can browse internet.


now i want to redirect all client to apache sever ( 127.0.0.1)

i try
sudo /etc/init.d/apache2 start
```
sudo /etc/init.d/apache2 start
```now if i go to 127.0.0.1 with my pc i can see the apache server home page.

```
ptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to-destination 127.0.0.1:80
``````
iptables -t nat -A POSTROUTING -j MASQUERADE
```but now the client stop browse. and can't loading web page. 
Why ?
how can i redirect client to 127.0.0.1 ?

---

### Post by Doug S on 2012-12-12
When you say "cliient", I assume that you mean a PC on your internal LAN.
It is difficult to know what is wrong without the context of your full iptables rule set.
Also, I am unable to set up your exact conditions on my test computers, so can not test my suggestions.
 
I wonder if packet routing through iptables gets into difficulties because of the re-direction to the local host. The suggestion is to try to redirect to one of the other network interfaces and to specify network interfaces. Of course this assumes that apache is listening to port 80 on all interfaces, which it does by default.
 
For example, if your internal network interface is eth0 and your external is eth1, try:```
sudo iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 80 -j DNAT --to-destination 192.168.0.10:80
```(replace 192.168.0.10 with your actual internal IP address.)

---

