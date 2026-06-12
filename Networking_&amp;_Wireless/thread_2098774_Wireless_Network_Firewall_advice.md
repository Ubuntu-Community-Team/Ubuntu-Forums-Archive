---
title: "Wireless Network Firewall advice?"
date: 2012-12-27
forum: Networking &amp; Wireless
---

### Post by Rayston on 2012-12-27
I have the following router 

[http://homesupport.cisco.com/en-us/support/routers/WRT54G2](http://homesupport.cisco.com/en-us/support/routers/WRT54G2)

Currently working with stock firmware. 

I was looking at DD-WRT here 

[http://www.dd-wrt.com/wiki/index.php/What_is_DD-WRT%3F](http://www.dd-wrt.com/wiki/index.php/What_is_DD-WRT%3F)

[http://www.dd-wrt.com/wiki/index.php/Linksys_WRT54G_v2.0](http://www.dd-wrt.com/wiki/index.php/Linksys_WRT54G_v2.0)

and also looking at various PC based Firewalls like these 

[http://www.smoothwall.org/](http://www.smoothwall.org/)

[http://www.techradar.com/us/news/software/applications/7-of-the-best-linux-firewalls-697177/2](http://www.techradar.com/us/news/software/applications/7-of-the-best-linux-firewalls-697177/2)

I have a spare laptop I can use to run the PC based Firewall OS of my choice. 

**Network will have the following on it. **

•2 Ubuntu 12.10 Laptops
•1 Windows 7 Laptop
•1 More laptop with undecided OS to serve as a file server.
•Phillips TV with Internet access (think Netflix) and a USB Port
•Netbook that will only connect to the home network locally to upload notes and download lowres video to view offline. 
•PSP that I very occasionally use to access my home network. 
•Kindle Fire HD

**I would like to have the following functionality from my network.**

•file server for sharing movies, music, etc. 
•Reasonably tight firewall protection.
•Web based configurability of the firewall(pretty standard)
•Incoming SSH/VPN/VNC access ( I want to be able to access the file server while away from home as well as the desktop of my laptops). Will mostly happen with above mentioned Netbook and sometimes the PSP. 

**My ultimate question is**

Should I go with DD-WRT? Or Smoothwall or other PC Based firewall solution? Both? Neither?

---

### Post by Pjotr123 on 2012-12-27
I advise Tomato for that router:
[https://sites.google.com/site/easylinuxtipsproject/tomato](https://sites.google.com/site/easylinuxtipsproject/tomato)

I have much better experience with Tomato, than with DD-WRT. More stable, more reliable, less buggy. :)

---

### Post by chadk5utc on 2012-12-27
I agree I would go with Tomato it will give you so much more configuration options and flexibility that Off the shelf stock devices do not.

---

### Post by ahallubuntu on 2012-12-27
I have had great luck with DD-WRT; I have run it on many routers and have not had stability problems; an uptime of over a year is not uncommon (by then someone has probably turned off the power once or twice anyway).

I have used Tomato also. Both will have decent firewalls, certainly adequate for what you need.  Yes, you could run a firewall on a spare PC, but that seem unnecessary.  Your Linksys router is probably on all the time anyway and consumes all of about 5 watts. Even your laptop will consume at least 10 watts (with screen dimmed) and probably would offer you no better protection than anything in DD-WRT or Tomato.  Your spare laptop could probably see better use somewhere else.

---

