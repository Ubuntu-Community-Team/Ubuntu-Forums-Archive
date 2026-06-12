---
title: "installation problem of Nagios + mrtg plugin in ubuntu"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by lefocus on 2009-01-29
hi, 
I have problem with installation of nagios plugins in ubuntu 8.10 server.
After installation of nagios-plugins-1.4.13, i cant find check_snmp and check_mrtgtraf in /usr/local/nagios/libexec why?
 
i did ..
1. Nagios had been installed and is working..
2. sudo apt-get install snmp
3. /nagios-plugins-1.4.13$ sudo ./configure  --with-nagios-user=nagios-with-nagios-group=nagios
 sudo make
 sudo make all

---

### Post by lefocus on 2009-01-29
[solved]
sorry..i did mistake 
false: /nagios-plugins-1.4.13$ sudo ./configure  --with-nagios-user=nagios-with-nagios-group=nagios
true: /nagios-plugins-1.4.13$ sudo ./configure  --with-nagios-user=nagios --with-nagios-group=nagios

---

