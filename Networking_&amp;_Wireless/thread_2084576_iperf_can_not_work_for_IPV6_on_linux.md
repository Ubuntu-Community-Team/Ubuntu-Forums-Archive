---
title: "iperf can not work for IPV6 on linux"
date: 2012-11-15
forum: Networking &amp; Wireless
---

### Post by ace120kobe on 2012-11-15
As title, iperf can not work for IPV6 on linux!
I just used iperf 2.0.5. 
There is a patch, but it is also not ok.
I have surveyed for many websites, and I am sure that I typed the right arguments.
Does anyone succeed? or it is still a bug in iperf?  
PLZ tell me~ thank you!!

---

### Post by lemming465 on 2012-11-19
Can you give examples of what you typed?  **iperf -V** has worked for me over IPv6 on a variety of platforms including both Redhat and Ubuntu Linux.  You might need to be using global scope addresses 2000::/3 rather than link-local scope fe80::/64 as I can't find any iperf options for specifying interfaces (aka IPv6 zones).  For diagnostic purposes output on the two systems of ```

ip address show
ip maddress show
ip -6 route show
ip -4 route show
```
would be enlightening.

---

