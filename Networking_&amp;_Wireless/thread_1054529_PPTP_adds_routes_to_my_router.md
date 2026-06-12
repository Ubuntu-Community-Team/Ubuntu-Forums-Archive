---
title: "PPTP adds routes to my router"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by wareagle on 2009-01-29
I have a PPTP server running on my home router.  When I connect to it from Ubuntu, my routing table adds two routes to 192.168.10.1/255.255.255.255 and to [WAN IP]/255.255.255.255. (192.168.10.1 is my router's LAN IP.)

This makes it so that instead of being tunneled through the VPN, connections to my router go out through the default gateway of whatever network my Ubuntu laptop is connected to.  This is a problem because the PPTP connection uses my router's LAN IP as the DNS server, and of course, the only way to route traffic to my router's LAN IP is through the VPN.

Is it possible to disable the adding of these routes?  I set up the VPN connection through the NetworkManager GUI.

---

### Post by wareagle on 2009-07-13
bump :p

---

### Post by superprash2003 on 2009-07-13
you could add routes manually which should overwrite [http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

