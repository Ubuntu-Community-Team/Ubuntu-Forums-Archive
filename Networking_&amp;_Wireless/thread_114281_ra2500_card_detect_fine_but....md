---
title: "ra2500 card detect fine but..."
date: 2006-01-08
forum: Networking &amp; Wireless
---

### Post by darknight on 2006-01-08
i've installed ubuntu 5.10 things seem to have gone ok so far except for my wireless card(ra2500 based) it detects the card fine and detects the network, i've tried a static ip and using dhcp neither allows me to access any sites or my router i cant ping the router either

---

### Post by gnu2tux on 2006-01-08
can you tell me what you get if you do:

$ifconfig

and 

$route

at the prompt (set router and Ubuntu up for DHCP first).

finally, what is the contents of /etc/resolv.conf:

$cat /etc/resolv.conf

With that information we will be able to diagnose the problem.

Regards,

Al.

---

