---
title: "connection timed out-dsl"
date: 2012-03-08
forum: Networking &amp; Wireless
---

### Post by gangar on 2012-03-08
I have a problem with my wired dsl-internet connection
pppoeconf works to connect with, I obtain an IP,and can browse the net for short time. 
BUT:
 About two minutes afterwards this message appears in firefox:no servers could be reached.
nslookup mot [www.google.com]("https://www.flashback.org/leave.php?u=http%3A%2F%2Fwww.google.com") yields 
;;connection timed out;no servers could be reached

cat /etc/resolv.conf gives two identical nameservers belonging to my isp.
nmap scan against these gives: host seems down.

 When I boot into windows there is no problems under the same dsl-connection. It also has worked fine with earlier versions. 
My guess is there is a problem with pppoeconf,but I am not sure.
When starting the pppoe connection I obtain IP's both for the eth0 interface as well as the ppp0 interface,but that has also occurred in earlier ubuntu-versions and shouldn't be the problem.
Any ideas anyone?

---

