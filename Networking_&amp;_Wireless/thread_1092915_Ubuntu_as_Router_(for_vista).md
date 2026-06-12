---
title: "Ubuntu as Router (for vista)"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by arcanewulf on 2009-03-10
My laptop has a broadcom wireless card that just died, and it shows up once every 10 times I start it up. I want to use the desktop in my room which has ubuntu 8.04 installed and connected wifi to my router to get internet to my laptop. 

I set up a dhcp server to use my ethernet card to listen for connections and assign ips from 192.168.5.40-192.168.5.60, with 192.168.5.1 as the gateway, and 192.168.5.255 broadcasting dhcp.

I hooked up a crossover cable between the laptop (vista) and the desktop (8.04) and assigned them ip's 192.168.5.43 and 47 respectively. I've tried both 192.168.5.0, .1, and .255 as the dns server, as well as for windows to configure it automatically. I can't get any connection between the two, I even tried toggling off a flag in vista that Microsoft says can be a problem when connecting to some routers' DHCP.

Any ideas? It will probably be months before I'll have hp fix my laptop, and weeks before I'll be able to get a usb wireless card. Thanks in advance

---

### Post by arcanewulf on 2009-03-10
I'm done working on it tonight, I won't check back til tomorrow night.

---

### Post by Adina on 2009-03-11
try to use the dns server that you use on your router.

---

