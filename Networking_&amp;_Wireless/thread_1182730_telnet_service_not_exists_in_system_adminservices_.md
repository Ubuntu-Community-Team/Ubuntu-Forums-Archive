---
title: "telnet service not exists in system admin/services in ubunto 9.04"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by hamza1982 on 2009-06-09
dears
i have problem with establish telnet session from windows client to ubunto 9.04 desktop client, i checked the services in ubunto to enable telnet service but it not exist.

your advice appreciated

regrds 
hamza

---

### Post by Evil Dax on 2009-06-09
have you installed the telnet server?
System, Synaptic Package Manager -> find telnet
or
terminal:
sudo apt-get install telnetd

---

