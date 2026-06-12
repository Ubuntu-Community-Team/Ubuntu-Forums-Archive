---
title: "IPv6 - Automatic Configuration not working"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by cprofitt on 2011-04-19
Hello all:  I just purchased a router that supports IPv6 and configured my eth0 to use IPv6. I have tried automatic and automatic, address only with no results.  My Windows 7 and OS X 10.6 boxes both work w/o issue of need to change settings.  I have done a bit of Google searching, but not found much in the way of useful advice. Can someone point me to a good article or let me know that the product is broken at this point.

---

### Post by koszta on 2011-04-19
it is not really clear what are you trying to ask... So you have a Linux box and trying to get IPv6 working on it?
Or is it the router that is the problem

This is a quick howto for IPv6 on Linux:
- to add a static address for your interface (otherwise router advertisement via ICMPv6 should give you address automaticaly) do:
```
ip -6 addr add <ADDR>/<PREFIX_LENGTH> dev <DEV>
```
- to add a static route (but again this should be done by router advertisement)
```
ip -6 route add default via <ADDR>
```

=> also check how is your firewall doing in ipv6 (iptables6 command if I remeber correctly => I think this just might be the issue, cause by default ipv6 is disabled in iptables... If you want to test it try ```
service iptables stop
``` 
If you actually want to have a working iptables6 firewall then good luck. REMEMBER that you need to allow A LOT of stuff from icmpv6 (for router advertisement & solicitation and friends to work...). I have actually not yet seen a good and stable configuration for iptables6 and icmpv6 = it is a tough one and probably requires the study of the RFC

---

### Post by koszta on 2011-04-19
you should also definitelly do 
ip -6 addr show dev eth0 to see if you have ipv6 addr assigned.... also see ip -6 route show 
also try traceroute6 and ping6

---

