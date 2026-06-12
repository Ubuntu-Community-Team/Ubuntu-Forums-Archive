---
title: "How to configure local domain in /etc/hosts style"
date: 2011-09-23
forum: Networking &amp; Wireless
---

### Post by luajunyi on 2011-09-23
Hi,

I would like to have machines(20+) in my private network to resolve domain names within the local network in the manner of a /etc/hosts file.

For instance, I want to translate 'dev' to 192.168.1.100, 'abc' to 192.168.1.101....

I can be accomplished by modifying /etc/hosts on every machine, but it's too tedious.

The router was a Ubuntu machine with DHCP enabled. It is also the DNS server in the network using bind9. I want to have bind do this DNS work but can only create a zone file like 'lo' and have 

dev.lo => 192.168.1.100

Yes, it's possible to create for each host a zone file and a respective db file, but its also kind of troublesome. 

Is there a way I can configure them all in one file? Like in /etc/hosts and have all machines in the private network resolve local domains like 'dev' and 'abc' correctly?

Thanks.

---

