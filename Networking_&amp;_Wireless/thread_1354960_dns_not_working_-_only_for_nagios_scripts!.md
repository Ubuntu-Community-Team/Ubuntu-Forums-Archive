---
title: "dns not working - only for nagios scripts?!"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by jmagnuss on 2009-12-14
After I did some ubuntu upgrades a while ago it seems some programs
can't resolve names.  nslookup works, the resolv.conf is fine (it was missing values originally).

If I do a check_http using a hostname, it times out
If I do it with the IP it works right away
ping and nslookup work on the hostname

Getting this with multiple hostnames, and it's not a web server thing since the same happens with check_tcp:

root@ubuntu:/etc/nagios3# /usr/lib/nagios/plugins/check_tcp -H
blah.blah.com -p 80
CRITICAL - Socket timeout after 10 seconds

root@ubuntu:/etc/nagios3# /usr/lib/nagios/plugins/check_tcp -H
xx.xx.xx.xx -p 80
TCP OK - 0.095 second response time on port
80|time=0.094805s;;;0.000000;10.000000

root@ubuntu:/etc/nagios3# nslookup blah.blah.com
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   blah.blah.com
Address: 7xx.xx.xx.xx

Thanks, this is annoying me.

---

### Post by ermannob on 2012-09-13
Hi,
I'm facing the same problem.
Did you find a solution?
I'm on ubuntu 12.04 LTS.

Thanks.
-ermannob

---

### Post by jonobr on 2012-09-13
From 2009 , I reckon he is long gone!!

---

### Post by ermannob on 2012-09-14
Well in the end it was the primary dns server that was not responding.
Nagios doesn't switch to the secondary (like all the other software on my machine, that's why I didn't notice that problem before), it just goes timeout and returns "offline" status.

So... fix your network interface config! ):P

---

