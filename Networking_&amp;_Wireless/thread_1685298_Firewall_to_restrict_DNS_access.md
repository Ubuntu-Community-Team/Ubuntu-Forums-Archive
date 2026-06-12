---
title: "Firewall to restrict DNS access"
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by ant2ne on 2011-02-10
Given: I'm an administrator of the network, but not of the computers that connect to that network. I set my DHCP server to hand out DNS as 192.168.1.3, which is my internal DNS server. And I set this DNS server to forward traffic to 208.67.222.222. And then I set up my OpenDNS account to filter out porn. What can I do to prevent the users from changing their local machines DNS server to whatever they want and bypass this filter? Can I set my external firewall to drop port 53 on outbound traffic that is NOT destined to IP 208.67.222.222? Would that work? I have a Linux firewall, what would be the IPchains/IPtables command to do this?

---

### Post by ant2ne on 2011-02-10
I think I found my answer...

[http://www.dd-wrt.com/wiki/index.php/OpenDNS](http://www.dd-wrt.com/wiki/index.php/OpenDNS)

---

