---
title: "Ubuntu 10.10 WAN/LAN issue"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by w14219 on 2011-05-06
**Server: **Ubuntu 10.10
**Application:** UFW, Squid, SquidGuard
 
 
**Issue:**
I have a web server on the LAN that is being NATed to an external IP address. From within the LAN, I cannot access the Public DNS'd address. The site times out.
 
From within the LAN I created an internal private DNS'd name (.local). All of the browsers work fine access the local site, however, at times the local site gives me a 404 error. The page cannot be displayed.
 
**Looking for:**
Why will the Public IP address not work for the internal LAN?
 
**Setup:**
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to- 8080
iptables -t nat -A POSTROUTING -s 172.20.0.0/16-j MASQUERADE
 
**Error:**
ERROR
The requested URL could not be retrieved
--------------------------------------------------------------------------------
The following error was encountered while trying to retrieve the URL:
[http://XXX.k12.wi.us/](http://XXX.k12.wi.us/)
 
Connection to xxx.xxx.xxx.xxx **(public IP) **failed.
The system returned: (110) Connection timed out
 
The remote host or network may be down. Please try the request again.
Your cache administrator is webmaster.

---

