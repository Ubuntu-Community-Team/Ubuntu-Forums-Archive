---
title: "How to enumerate all network devices connected to router?"
date: 2013-02-09
forum: Networking &amp; Wireless
---

### Post by jiapei100 on 2013-02-09
Hi, all:

This is a C++ programming issue. I want to enumerate all network devices connected to the router. I was thinking to **for_each "ping"** from my desktop to every IP address under the same IP segment. However, there seems to be at least a firewall issue. If there is a firewall blocking my desktop's IP and one networking device's IP, **ping** may fail too.


So, how can I use C++ to retrieve all network devices that have been connected to the router?



Best Regards
Pei

---

### Post by alexii on 2013-02-10
I can't help you with C++, but if ping is not a solution, you could send ARP broadcasts asking who has each IP in the subnet and see what replies.

---

