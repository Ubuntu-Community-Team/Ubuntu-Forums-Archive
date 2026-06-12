---
title: "DNS issues"
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by norsemonkey on 2006-06-25
Ok...here's the problem:
Whenever I start the GUI (by typing startx into the terminal) by resolv.conf file gets reset.  The problem is that by default it shows 3 lines:
search domain.actdsltmp
nameserver 192.168.0.1
nameserver 205.171.3.65

This results in patchy website access and unresolved domain names.  After much research I have discovered that my ISP's DNS's are 205.171.2.65 and 205.171.3.65
My modem/router is knows the 2 DNS servers, but for some reason my computer won't access those.

So what I want to do is either
1. configure Ubuntu so that it will automatically take the DNS's from the router
or
2. configure Ubuntu so that resolv.conf will always contain the two nameservers without resetting.

---

### Post by scxtt on 2006-06-25
what's your "Gateway address" listed as under your network settings (System --> Administration --> Networking : click on your active eth connection) ... i have mine set to the IP of my router (which knows the DNS) and it gets them everytime ... are you using DHCP?

---

