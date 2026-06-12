---
title: "VPN gone bad | not connecting to internet without VPN"
date: 2013-03-21
forum: Networking &amp; Wireless
---

### Post by AshyGator on 2013-03-21
Hi , 
     I had absolutely no problem with Ubuntu 12.04 untill I  installed CISCO ANYCONNECT VPN , after connecting to a particular VPN  network , when I try to use the network without vpn , it just doesn't  work ! Tried rebooting, restarting network interfaces, disabling the vpn  adapter .. wired .. wireless .. doesnt work . Any help is appreciated.  Thank you.

---

### Post by sanderj on 2013-03-22
What is the output of:

```
ip route show
mtr -nrc2 8.8.8.8
```

Post it here

---

### Post by AshyGator on 2013-03-22
I think I got the solution 
my dns config file (/etc/resolv.conf) mislead all the urls appending my company name as suffix . eg: google.<my_company>.com . Resolved it by removing the company's dns server in that file.:popcorn:):P

---

