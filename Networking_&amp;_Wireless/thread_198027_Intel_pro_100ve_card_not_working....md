---
title: "Intel pro 100/ve card not working..."
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by tdrusk on 2006-06-16
Any tutorials I can follow to make it work? I really like linux. 
The card activates, but when I try to load a page it doesn't work.

---

### Post by deepnum on 2006-06-16
i have the same ethernet card on my new laptop that i recently installed ubuntu on. I was trying to connect to the internet through my home router. i could see the linksys router (typed 192.168.1.1 in the address bar of firefox and got to the router's web based admin page) but i couldn't connect to the internet

on the forum i found the answer to my problem
1) type "about:config" into firefox's address bar
2) type "ipv" into the filter
3) toggle the value for network.dns.disableIPv6 to true (just double click it i think)

once i did that, everything was peachy :) 

maybe this will work for you

---

### Post by tdm on 2008-02-09
This worked great!!! Thanks!

---

