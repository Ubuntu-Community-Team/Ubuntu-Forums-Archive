---
title: "[WLAN/LAN] Downloads hang when they reach about 1mb/s"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by matzipan on 2010-07-15
The setup: 
Siemens Gigaset WLAN/LAN Router
Ubuntu 10.04 Desktop/Windows 7 laptop via WLAN
Ubuntu 10.04 Server via LAN

The problem: downloads on Ubuntu (WLAN laptop, LAN server) always hang, no matter what software I use: wget, chromium, firefox. Apt only slows down to about 20-30 kb/s on LOCAL repos. 

The proof: 7 gets along most of the time with the router, it sometimes has some DHCP syncing problems. The syncing problem does not appear in Ubuntu, so it is strictly Windows related. When I run the Ubuntu on the laptop in VMware on Windows, the downloads work ok.

I have read some posts that state that the problem is related to the DNS resolving of the router, as my DNS Server is pointing to the router. Tried the Google DNS Servers, and the problem was the same. 

What could the problem be?

---

