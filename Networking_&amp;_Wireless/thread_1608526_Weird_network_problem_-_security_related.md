---
title: "Weird network problem - security related?"
date: 2010-10-29
forum: Networking &amp; Wireless
---

### Post by d1zzy on 2010-10-29
I'm using stock rsyslog v4.2.0 running on an Ubuntu Lucid x64 server with two interfaces. The "main" NIC eth0 has a 10.x.y.z/24 address; eth1 has a 172.16.a.b/24 address. There are no iptables rules or out of the ordinary routing at present. Rsyslog is set up to listen on **all** interfaces and log to MySQL via memory/flat file if necessitated by throughput, as per the instructions on the rsyslog site. Any logs sent to eth0 get into rsyslog no problem.

Anything sent via eth1 do not get logged. I can see the traffic coming in using "tcpdump -vvi eth1 udp port 514" but rsyslog doesn't seem to register it. I tried it using syslog4j, also with no results. I cobbled together a dumb, undiscriminating UDP listener which cannot see what's coming in either. Again if I send the traffic to eth0 both syslog4j and my UDP listener can see the logs coming in fine.

I did packet captures on identical logs coming in on eth0 and eth1 and they don't differ in any substantive way (only in date/time and checksum).

EDIT: If I connect directly to the 172.16.a/24 LAN I can send logs to the box which are received. Logs *not* on that LAN are received via tcpdump, just not by rsyslog, syslog4j or udplistener.jar (hence the "off-LAN" title).

HELP! This is driving me nuts!!

Cheers

---

