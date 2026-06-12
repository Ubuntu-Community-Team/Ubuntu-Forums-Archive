---
title: "application specific routing on multiple gateways"
date: 2011-06-03
forum: Networking &amp; Wireless
---

### Post by ratzrul on 2011-06-03
Hi guys,
I have two active internet connections set up using eth1 (192.168.2.6/24,gw:192.168.2.1) and wlan0 (192.168.1.101/gw:192.168.1.254) to my home pc that hosts a small apache server. I would like to setup apache server to route its data through eth1 while all other data being sent through the wlan0 interface. I already set up the webserver to only listen to one interface but when I'm using wlan0 as my default gateway all remote clients timeout from the webserver. I would like to know how I would configure both default routes to act simultaneously while filtering packets from a specific source port (80) to a certain route. 

A tcpdump -i eth1 port 80 while im connected to wireless shows packets arriving to the interface how ever no replies are sent.
I also tried using iptables -t mangle to mark packets and redirect them using tables, didn't work out since packets are all generated at localhost and they never parse through PREROUTING table. 

I'm a real noob when it comes to linux networking so any assistance is appreciated guys! Thanks

---

### Post by ratzrul on 2011-06-05
bump... any ideas?

---

