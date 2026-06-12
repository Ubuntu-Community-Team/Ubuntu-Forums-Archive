---
title: "Internet Connection Sharing via Firestarter"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by Si105 on 2010-02-05
Hello,

At my home I am using firestarter to connect my XBOX 360 to the internet and it works perfectly, never crashes etc and I get a moderate NAT which I've never experienced any problems in having.

I have my devices set up like this

eth0 - ifconfig eth0 192.168.2.1 netmask 255.255.255.0 broadcast 192.168.2.255
XBOX - 192.168.2.10 netmask 255.255.255.0 broadcast 192.168.255 gateway 192.168.2.1

This configuration works perfectly on my router at my house which has the IP of 192.168.0.1

However at my friends house he has a router with the IP adress of 192.168.2.10 or 192.168.2.7*, Sorry I don't remember exactly but I'll find out tonight. I have tried changing my IP settings on my xbox and eth0 to no avail. I noticed instantly that the XBOX IP is the same as my friends router. If anyone could help me out with what the new settings would be, or simply changing the router's IP, I would be very gratefull

However there is also an issue with the DNS servers. I can't find them anywhere on the router or on the router box itself. I heard that I could point it towards my default gateway however. 

Thanks for reading

---

### Post by Iowan on 2010-02-05
DHCP might make the machine more "mobile" - but I'm not sure what that might do to the firewall...

---

### Post by Si105 on 2010-02-08
Ok cheers,

I'll wait I get my new laptop then try it.

---

