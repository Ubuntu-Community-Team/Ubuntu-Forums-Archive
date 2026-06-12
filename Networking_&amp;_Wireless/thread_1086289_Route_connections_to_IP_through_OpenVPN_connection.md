---
title: "Route connections to IP through OpenVPN connection"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by grundunkus on 2009-03-03
I have a network in my house, a network in my office and some servers in a colocation facility.

The servers in the datacentre can be accessed by IP over the internet from the network in the office, but not the network in my house. I have a VPN in the office which I can connect to from home. 

Is there an easy way to configure OpenVPN to make all connections to the servers in the datacentre route through the VPN connection to the office when I am connected from home, so I can effectively connect 'directly' to those boxes at home (but have the connections transparently route through the VPN)?

I have searched high and low for simple explanations on setting up routing but everything is far too advanced for my virtually nonexistent understanding of the concepts involved.

---

### Post by PilotJLR on 2009-03-03
Yes... with OpenVPN, you can push routes out to endpoints. So, if you can openvpn into your office, then you could setup an openvpn server there to push routes to the subnet(s) to your colo.

---

### Post by grundunkus on 2009-03-03
Yes, but how?

---

### Post by PilotJLR on 2009-03-05
This howto helped me a lot when I was setting up a few openvpn's:

[http://openvpn.net/index.php/documentation/howto.html](http://openvpn.net/index.php/documentation/howto.html)

In particular, try this section:
[http://openvpn.net/index.php/documentation/howto.html#redirect](http://openvpn.net/index.php/documentation/howto.html#redirect)

That may be the simplest... if you push all traffic through the VPN, then the IP route to the colo would be determined by the VPN gateway.

---

### Post by grundunkus on 2009-03-23
The 'redirect' section of the HOWTO covers redirecting all traffic through the VPN. My initial post was not quite clear on this, but I definitely do not want this to happen. I only want traffic to the servers in the datacentre to go through the VPN.

I actually solved my problem myself in the end by experimenting with the route command.

My home router is on 192.168.0.1, but the router in the office is on 172.16.0.254 and is accessible from my box when I'm on the vpn so I went

route add -net 300.300.300.100 netmask 255.255.255.240 gateway 172.16.0.254 dev tap0

300.300.300.100 is the (clearly) bogus internet IP i wanted to route through the VPN. So after I managed to get that to work by manually adding the route, I just made sure the route-gateway setting was pushed in my openvpn server.conf as 172.16.0.254, then I added 

push "route 300.300.300.100 255.255.255.240"

and it all works fine. Hopefully this helps someone else.

---

