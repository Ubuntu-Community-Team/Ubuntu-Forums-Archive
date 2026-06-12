---
title: "2 IPs for one router as DHCP - connection to Internet fails"
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by ales on 2006-06-22
I have noticed that my router has IP 10.0.0.138. This adress in my opinion is also the adres of DHCP serves cause router assigns the IP adresses to my network cards. 

My Internet connection is not working cause when I look network configuration in Ubuntu , there are two DHCP servers 10.0.0.138 and second somethng like 168.x.x.x. The INternet works only if there isonly one DNS but ubuntu usually configures it so that there are 2 DNS 10.0.0.138 and 168.x.x.x. I think it's cales primaryand secondary DNSwhat can b wrong.

---

### Post by Iowan on 2006-06-23
DNS or DHCP? 
Having more than one DNS server is not unusual (usually tagged primary/secondary... as you mentioned), multiple DHCP servers will probably cause conflicts and/or other problems. The client generally doesn't know/care where the DHCP server is  - it just sends out a request for an address, and the first response wins. It'd be curious (maybe more than curious) to know where that phantom DHCP server is coming from - or if the router is double-dealing.

---

