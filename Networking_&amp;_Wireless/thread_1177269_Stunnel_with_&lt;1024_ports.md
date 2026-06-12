---
title: "Stunnel with &lt;1024 ports"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by msetzerii on 2009-06-03
I'm trying to get access to gmail thru the stunnel ports of 995 and 465.

I have installed Pegasus Mail via Wine, and configured it to use ports 20995 and 20465 on the 127.0.0.1, and have setup stunnel to map these ports to the correct ipaddresses and ports. Unfortunately, I have not been able to it to work with ubuntu 9.04. With Fedora 10 this process works fine.

I have been able to get it to work using my fedora machine with port 20995 and 20465 and it does work, so I am thinking it is something to do with port <1024. 

I tried a number of things with ufw and iptables, but still no luck. 

Hoping someone may have had a similar situations, and come up with a solution.

---

