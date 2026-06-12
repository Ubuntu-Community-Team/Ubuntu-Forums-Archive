---
title: "Setting up NAT and FileZilla through Shorewall"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by Stronghol on 2010-08-03
After about a week of struggling to get vsftpd running on my server, I  decided to say forget it (didn't want people connecting directly into my firewall anyway) and set up filezilla on my internal machine. 
So, how would I get FTP running on my internal machine? 
I have a static IP, an Ubuntu 9.10 gateway/firewall box, Shorewall, and an internal windows network. 
So, what lines would I need to add, and what modules would I need to load, to point everything coming in on FTP to 192.168.1.68?
I have ip_conntrack_ftp and nf_nat_ftp modules loaded. 
In rules I have 
DNAT    net     loc:192.168.0.68        tcp     20:21
Its not working, so wha'd I miss?

---

