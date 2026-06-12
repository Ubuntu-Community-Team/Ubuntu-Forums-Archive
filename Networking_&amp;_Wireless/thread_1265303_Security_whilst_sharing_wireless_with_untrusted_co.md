---
title: "Security whilst sharing wireless with untrusted computers"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by ngl984 on 2009-09-13
Hi - 

I have a slightly different home setup where I am sharing my internet connection with a neighbour via wireless. 

My gateway is an ubuntu server has multiple eth cards as follows:
eth0 internet ip
eth1 My LAN 10.0.1.0/24
eth2 Wireless LAN 10.0.2.0/24
tun0 (openvpn server - routed ip) 10.0.3.0/24

I have setup all my services to only listen on eth1 for security reasons and also firewalled. vpn server listens on eth2, and routes everything through tun0.

Internet connection is working well, and using openvpn for extra security however not critical. I'm trying to work out some way to allow upnp on the server to map ports to the WLAN clients but dont want to open up a security hole to my lan or server.

Is there a way to run upnp for LAN and WLAN without allowing full access to the ubuntu server. i.e. only map ports from internet to the upnp client IP?

- Can a client computer send a request for a upnp port map for anything but itself?
- Can a client computer open a port from the server to itself?

upnp info on google/net seems a bit technical and lacking info on the affect on firewalls.

- thanks, ngl984

P.S. I'm using shorewall for easy of administration but happy to change if necessary.

---

