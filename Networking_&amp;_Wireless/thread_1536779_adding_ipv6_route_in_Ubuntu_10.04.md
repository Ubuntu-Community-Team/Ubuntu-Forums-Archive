---
title: "adding ipv6 route in Ubuntu 10.04"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by jdysinger on 2010-07-22
Has anyone had issues adding an IPv6 route in Ubuntu 10.04? 
 
Just curious as I've done:
 
#route --inet6 add 2002:20:20:20::/64 gw 2002:20:20:20::1 dev eth0
 
~and~
# ip -6 route add 2002:20:20:20::/64 via 2002:20:20:20::1
 
and neither worked. Using the route command returned "SIOCADDR: Invalid Argument" and the ip command returned "RTNETLINK: Invalid Argument".
 
I installed radvd and still have the same issues. 
 
I googled the terms and found someone who believes it to be a bug. Is there a workaround or fix or am I just not doing something correctly? 
 
Thanks! 
(ps, those ipv6 addresses are not real)

---

