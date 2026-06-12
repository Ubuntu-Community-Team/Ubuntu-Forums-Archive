---
title: "On ICMP services"
date: 2010-10-02
forum: Networking &amp; Wireless
---

### Post by Aetixintro on 2010-10-02
Hi all

I'd like to point out a few nice things about ICMP that may serve you well.
It's mostly pointed out that ICMP operates by _no_ particular port, it's not entirely true, I've found out. Here are my findings:
Ping/Whois - port 43
Traceroute - ports 33400-33500 (I think you can limit this.)
Lookup is indeed using a host of mechanisms.
Portscan - ports 33500-33600, you can possibly add 1443 and 40000-61000 (These are only suggested. Please, also remember that these are OUTGOING, no extra risk for incoming.)
Finger (yet to test for Finger)

Conclusion: it pays off to investigate and ICMP is not so isolated behind a firewall (eg. Firestarter) as some people like to think. I'll develop this. Cheers! :)

[Edit:] You can correlate yourself by using iptstate.```
sudo iptstate
```It's a very useful program.
You should also keep the eyes on iptables and the firewall.

[Edit2:] Netstat and Devices are internal issues of the computer whether you like to 
have the data from these 2 services while being online or not.

---

