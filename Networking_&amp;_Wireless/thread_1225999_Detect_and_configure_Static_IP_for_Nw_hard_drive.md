---
title: "Detect and configure Static IP for N/w hard drive"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by Chetan26 on 2009-07-29
Hi ,
     I have an Iomega  Network Hardrive 500GB. 
     I have connected it to my network  but iam not able to access it from 
     my UBuntu  machine. 
     I want to detect it and configure a static IP address to it .
     Could you please provide help  .

THanks
Chetan

---

### Post by Iowan on 2009-07-29
I presume you've seen [this]("https://iomega-na-en.custhelp.com/cgi-bin/iomega_na_en.cfg/php/enduser/std_adp.php?p_faqid=20886&p_created=1228595750&p_sid=e1vr*3Ej&p_lva=21149&p_li=") page.  If you have DHCP server and NAS drive gets address, you can check DHCP leases, or **ping -b X.X.X.0** (where X.X.X.0 is your local network address - like 192.168.1.0).

---

