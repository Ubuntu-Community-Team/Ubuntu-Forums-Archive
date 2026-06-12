---
title: "Squid Configuration File"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by honey_bee on 2011-01-03
Hi,
     I want to discuss about squid configuration file. What is the batter approach that before configuring squid is it good that copy the original file like as following

cp /etc/squid/squid.conf /etc/squid/squid.conf.bak

or move it and create a new empty file in /squid and write our rules in it.The benefit of creating own /squid.conf file is to read it and simplicity of rules instead to scroll up and down the copy of original file which has almost 3,000 lines.

mv /etc/squid.conf /etc/squid.back

#touch /etc/squid.conf

please guide me the professional approach.

thanks
honey.

---

