---
title: "Network is unreacheable"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by albertoramirez on 2006-06-28
Recently installed Kubuntu 6.06 at work, in order to show my office mates how Linux works and looks, but can't get the network connection to work.  I've issued all the parameters (static IP, DNS, gateway, etc).

How can I diagnose the problem.

And other question, where do I configure the workgroup name?

Thanks

---

### Post by dixonstalbert on 2006-06-28
hi alberto

open terminal and type

ifconfig 

see what it tells you

also try

ping 127.0.0.1 to see if tcpip is working okay
ping <ip address of something else on network>

ping in ubuntu will keep going forever or until you press ctrl-c

---

### Post by albertoramirez on 2006-06-29
Thank you Dixon!

Got it working, the information abour IPs and stuff was wrong!

:D

---

