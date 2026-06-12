---
title: "configuring static ip address behind router"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by thundercracker on 2011-09-02
I am trying to set up a a web server using an old computer and ubuntu, so far I have installed Ubuntu and have done all the basic set up, but I having trouble getting the server and my network configured. My server does have internet access and I can ping ip address.

I am trying to figure out where to enter the static IP I ordered, and where to put the local static IP. My server is behind a router and I believe I setup up the port forwarding correctly. I have also configured my modem to forward the static ip to the router, but there is no place to enter the static ip on that interface.

I have also configured my interfaces file with the static local ip, so I'm trying to figure out what to do next so I can access my webpages on my server through the internet.

EDIT: Although I know this doesn't exactly pertain to Ubuntu, I don't really know where else to get help with this kind of thing, would I need to set up the router with the static IP my isp gave me since the modem is forwarding it to the router?

---

### Post by thundercracker on 2011-09-18
bump

---

### Post by haqking on 2011-09-18
> **thundercracker said:**
> bump

The static typically will be assigned to your router WAN port, then requests for port 80 should be forwarded to your LAN IP that is hosting the webserver.

You make your server a static private IP such as 192.168.0.2 as your router LAN port is probably 192.168.0.1 or similar

The static IP from your ISP goes on your WAN connection then those requests are forwarded to your local LAN IP.

See here to configure static on your server [https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html)

You could also look at dynamic DNS if you want to continue using a dynamic from your ISP [http://dyn.com/dns/dyndns-free/](http://dyn.com/dns/dyndns-free/)

also read here [https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

another way would be to DMZ it but that will require you firewall the actual server, as with port forwarding you are protected from the big bad net by the router firewall ;-)

---

### Post by thundercracker on 2011-09-18
ty, it'll be a couple days before I'll have a chance to work with my server again, so as soon as I do, I'll let you know how it goes

---

