---
title: "ubuntu 12.04 snort error"
date: 2013-01-13
forum: Networking &amp; Wireless
---

### Post by jacenty on 2013-01-13
Hi, I'm testing snort wokrin as a daemon, I checked a simple rule with ICMP and it puts it to the logs.

I tried sth more complicated, a rule logging DNS requests
"alert udp ![$SMTP_SERVERS,$DNS_SERVERS] any -> $DNS_SERVERS 53 (msg:....etc"

in snort.conf file there are:
ipvar HOME_NET any
ipvar DNS_SERVERS $HOME_NET
ipvar SMTP_SERVERS $HOME_NET

when launching snort with -T parameter to check the rules it says:
"ERROR /etc/snort/rules/file.rules(5) !any is not allowed: ![$SMTP_SERVERS,$DNS_SERVERS].
Fatal error quitting"

what could be the problem ? what to check first
please help

---

