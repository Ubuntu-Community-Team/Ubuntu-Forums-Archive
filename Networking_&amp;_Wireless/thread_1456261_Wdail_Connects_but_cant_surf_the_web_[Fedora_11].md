---
title: "Wdail Connects but cant surf the web [Fedora 11]"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by aswinbabuk on 2010-04-16
I installed Fedora 11 and configured my /etc/wvdial.conf as follows:

[Dialer defaults]
Modem = /dev/ttyUSB0
Baud = 230400
Phone = #777
Init1 = ATZ
Stupid Mode = 1
Dial Command = ATDT
Username = username
Password = password
PPPD Options = crtcts multilink usepeerdns lock defaultroute

and, etc/resolv.conf as follows:

nameserver 218.248.240.181
nameserver 208.67.220.220

This configuration works just fine in ubuntu in which i can browse the web. But after installing Fedora, net connect but I am not able to load a single webpage. I am able to ping a DNS Server, but not any other server. Please help me, I need help for this fast!:confused:

---

