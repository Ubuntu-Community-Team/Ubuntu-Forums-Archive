---
title: "routing"
date: 2010-12-18
forum: Networking &amp; Wireless
---

### Post by chezerian on 2010-12-18
I have tried to follow the routing document but haven't had any success in implementing the following setup.


modem/router<--wifi-->PC<--ethernet-->openwrt<--wifi-->ipod / other wifi stuff.


I would like my ipod and other wireless stuff to get an IP from the modem.router if possible.

How should i proceed (on the PC, i can ask for openwrt help on the openwrt forum).

---

### Post by chezerian on 2010-12-20
bump

---

### Post by fragtion on 2010-12-20
If they're all on the same bridged network, DHCP should provide the IP no problem, if not, you simply need to do DHCP forwarding I'd imagine? Sounds to me like you just need to properly bridge all these interfaces together though

---

### Post by chezerian on 2010-12-21
How ?

---

### Post by SeijiSensei on 2010-12-21
You need an application to relay DHCP requests through *all* the intermediate routers.  For Linux machines, take a look at

[http://packages.ubuntu.com/maverick/dhcp-helper](http://packages.ubuntu.com/maverick/dhcp-helper)
[http://packages.ubuntu.com/maverick/dhcp3-relay](http://packages.ubuntu.com/maverick/dhcp3-relay)

This could still be very difficult to implement if the router behind the openwrt box provides a DHCP server.  You'll need to figure out how to relay the requests through that router as well.

Masquerading the network behind the openwrt box with iptables is a whole lot easier.

---

