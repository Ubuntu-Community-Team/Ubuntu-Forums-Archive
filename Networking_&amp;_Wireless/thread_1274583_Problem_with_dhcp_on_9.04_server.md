---
title: "Problem with dhcp on 9.04 server"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by gixpaulie on 2009-09-24
hi all
 
i am trying to convert a old machine into another firewall but having a problem with the dhcp on the internal side this is what i have and what im trying to do :-
 
 
map of what im doing is :- cable modem > router/firewall > the old machine (as another firewall) > switch > all other computer connect 
 
right the connection from the old machine to the router/firewall works fine and get the internet no problem at all, but the connection from the old machine to the other computer does not work has the dhcp is configured to run on the nic going to the other computers but when the other computers try to get a ip it comes up with the ip that means the dhcp server cant be found or did not respond.
 
the two nic are configured as follows
 
nic 1 going to the router/firewall ( one that works) 
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
 
nic 2 going to the other machine which the dhcp runs 
 
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.1.2
 
but the dhcp does not assign ip's to the other machine 
 
any ideas what im doing wrong 
 
many thanks

---

### Post by Iowan on 2009-09-24
If you're using **dhcp3** for server, what is in */etc/dhcp3/dhcpd.conf*?

---

### Post by gixpaulie on 2009-09-26
hi
 
 
dont worry i sorted it , instead of having static i changed it to dhcp logical sollution and it worked
 
 
thanks

---

