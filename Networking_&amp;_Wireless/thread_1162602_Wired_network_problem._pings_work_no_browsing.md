---
title: "Wired network problem. pings work no browsing"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by Yonco on 2009-05-17
Hi Guys.
I've got a network problem which I can't seem to be able to resolve -
I've recently changed my ECI B-FOCUS 270PR adsl modem/router from modem configuration (pppoe) into router configuration (pppoa).
the IP assignment with DHCP works ok. I can get it to connect the network via wired connection into the router's hub. (eth0)
when I ping it resolves all the addresses and pings ok.
only when I try loading a page with the browser or activate apt-get it contacts the site, and waits forever for a response from the site. (or headers in the apt-get case).
I currently have no firewall installed.
When my modem was in pppoe configuration (not as a router) the connection worked ok.
When I'm using [vista[IMG]http://images.intellitxt.com/ast/adTypes/mag-glass_10x10.gif[/IMG]]("http://www.ubuntux.org/node/9011#") the connection in the current configuration it works ok.
The problem persists either when using my desktop (kubuntu 8.10) or using my laptop (kubuntu 9.04) and also when booting from the live CD.
 Will appreciate any help trying to resolve the problem.
Let me know if you need any more information
many thanks.
Yoni.

---

### Post by superprash2003 on 2009-05-18
ensure that firefox is not in offline mode ( File->Work offline)
try opening [http://74.125.67.100](http://74.125.67.100) , does google open?

---

### Post by Yonco on 2009-05-18
> **superprash2003 said:**
> ensure that firefox is not in offline mode ( File->Work offline)
try opening [http://74.125.67.100](http://74.125.67.100) , does google open?

thanks for the reply. 
Firefox is not in offline mode. 
[http://74.125.67.100](http://74.125.67.100) doesn't connect to google. it just writes waiting for 74.125.67.100 and stays that way.

---

### Post by chili555 on 2009-05-18
Please post:```
cat /etc/resolv.conf
```

---

