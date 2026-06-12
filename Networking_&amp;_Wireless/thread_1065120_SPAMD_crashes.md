---
title: "SPAMD crashes"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by mesh2005 on 2009-02-09
I installed SPAM Assassin on my machine and so far I haven't been able to make it work. Here are a few lines of the log file:

Feb  9 13:18:42 laptop spampd[7689]: Starting "1" children 
Feb  9 13:18:42 laptop spampd[8023]: Child Preforked (8023)  
Feb  9 13:18:42 laptop spampd[7690]: 2009/02/09-13:18:42 CONNECT TCP Peer: "127.0.0.1:36479" Local: "127.0.0.1:783"  
Feb  9 13:18:42 laptop spampd[7690]: Initiated Server 
Feb  9 13:18:42 laptop spampd[7690]: WARNING!! Error in process_request eval block: /usr/sbin/spampd: socket connect failure: 11

I used netstat -pnat and I can see that the port 783 is there but no program is associated with it? Also, I tried to telnet 127.0.0.1 783 but I got: "connection was closed by foreign host".

Any ideas?

Thank you.

---

