---
title: "Munin SNMP problem"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by jbcola on 2010-03-21
Hello,

I tried to configure munin to collect SNMP data from my DD-WRT router, but it fails with these errors:
(On ubuntu 8.04 LTS)

root@eserver:/etc/munin/plugins# munin-node-configure --suggest --snmp 192.168.1.1
Odd number of elements in hash assignment at /usr/local/share/perl/5.8.8/Net/SNMP.pm line 2276, <PLUG> line 42.
Odd number of elements in hash assignment at /usr/local/share/perl/5.8.8/Net/SNMP.pm line 2276, <PLUG> line 42.
Odd number of elements in hash assignment at /usr/local/share/perl/5.8.8/Net/SNMP.pm line 2276, <PLUG> line 42.
Odd number of elements in hash assignment at /usr/local/share/perl/5.8.8/Net/SNMP.pm line 2276, <PLUG> line 42.
Odd number of elements in hash assignment at /usr/local/share/perl/5.8.8/Net/SNMP.pm line 2276, <PLUG> line 42.
Odd number of elements in hash assignment at /usr/local/share/perl/5.8.8/Net/SNMP.pm line 2276, <PLUG> line 42.
Odd number of elements in hash assignment at /usr/local/share/perl/5.8.8/Net/SNMP.pm line 2276, <PLUG> line 42.
Odd number of elements in hash assignment at /usr/local/share/perl/5.8.8/Net/SNMP.pm line 2276, <PLUG> line 42.
Odd number of elements in hash assignment at /usr/local/share/perl/5.8.8/Net/SNMP.pm line 2276, <PLUG> line 42.
Odd number of elements in hash assignment at /usr/local/share/perl/5.8.8/Net/SNMP.pm line 2276, <PLUG> line 42.
Odd number of elements in hash assignment at /usr/local/share/perl/5.8.8/Net/SNMP.pm line 2276, <PLUG> line 42.
Odd number of elements in hash assignment at /usr/local/share/perl/5.8.8/Net/SNMP.pm line 2276, <PLUG> line 42.


An snmp walk works correctly, should i fill a bug on the munin page?

---

