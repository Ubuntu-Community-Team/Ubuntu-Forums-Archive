---
title: "lan and usb modem dont work simultaneously"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by gallaharsha on 2009-03-26
Hi,
I have LAN ethernet connected to my comp.Also i have an Idea Netsetter usb modem data card. The problem is I want to connect to internet using data card while LAN is still connected. When I connect to LAN I am not able to use the Internet via Data card, it works once I disconnect my LAN cable. Can somebody help me out regarding this. Few days back I faced the same issue and I solved it by deleting the AUto eth0 and creating a new entry with manual settings, but since i installed a fresh copy of ubuntu i dont know how to get around this time.

Thanks in advance

---

### Post by namaku0 on 2009-03-26
Read this article:
[http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

This article may help too:
[http://www.cyberciti.biz/faq/how-to-find-gateway-ip-address/](http://www.cyberciti.biz/faq/how-to-find-gateway-ip-address/)

---

### Post by meredin on 2009-03-26
I've been having the same problem while using 8.10 desktop. my setup is a local wired network with no Internet connection so for Internet I use a mobile broadband stick.

Unfortunately if the Ethernet cable for the LAN is plugged in the Auto eth0 connection over rode the mobile broadband so I couldn't use it.

So far I've got a partial solution 

right clicking on the NetworkManager applet clicking on edit connections
under the wired tab select Auto eth0 and select edit unselect system setting then select the IPv4 tab and in the method dropdown box select local-link only. then OK

then select the usb connection mine was under the mobile broadband tab
select connect automatically and system setting. then under the IPv4 tab in the method drop down box select Automatic (ppp) addresses only then OK

this was found by trial & error... and has one annoying problem in that every-time I reboot a duplicate Auto eth0 connection appears which I have to delete before it all works!

could anyone let me know if there's a better way to do this and how do I stop that duplicate Auto eth0 connection appearing after each reboot?

---

