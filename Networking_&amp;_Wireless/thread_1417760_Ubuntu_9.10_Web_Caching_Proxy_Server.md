---
title: "Ubuntu 9.10 Web Caching Proxy Server"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by Theoutdoorsman on 2010-02-27
I'd like to create a web-caching proxy server for my home network. Can anyone assist? I need to know what software applications would be most beneficial for this purpose, as well as most user friendly. If not available via the package manager, I will likely need some advice on program installation and configuration. To give you and idea as to the network topology, I will be using one pc as my server (S) which will be connected directly to my access point. From the server (S), I will be connected to my wireless router. My main pc (pc1), will will be a wired connection to the server (S). My other two pc's (pc2 and pc3) will need a wireless connection to the router. If anyone can/will assist me in setting this up, it would be most appreciated. Thanks in advance!


BTW.... I am running Ubuntu 9.10.

---

### Post by Charly85551 on 2010-02-28
Hi, you forgot to tell us for what purpose you would like to set up a web caching proxy. The main reason for me is to set up a local network which is protected against the internet! But in your description pc2 & 3 are directly connected to the router any way. And increased protection for a single pc can be done with local firewall software as well. Check for example for *ipkungfu* as a local firewall for pc1. It's not too difficult to install. Just make sure it is switched on every time you boot your machine (which I forgot the first time I used it and then got shocked when I started testing the firewall:mad:)
cheers
charly85551

---

### Post by Theoutdoorsman on 2010-02-28
The purpose of the proxy server would be to cache visited web pages. The server will sit between the router and the access point.

---

### Post by Theoutdoorsman on 2010-03-08
I still haven't figured this out. If anyone can assist, your help would be most appreciated. I am trying to use the GADMIN-SQUID application. Too, I can successfully ping the router from all of my client pc's and the ubuntu machine. But, for the life of me, can't figure out how to get the network up. Do I need to use a crossover cable between the server and router?

---

### Post by toosneaky on 2010-03-15
I never got on with gadmin, squids config files are really good. post your iptables/ebtables and squid config and ill have a look.

---

