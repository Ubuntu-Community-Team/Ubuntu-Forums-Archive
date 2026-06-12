---
title: "No traffic passing through Bridge."
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by A.Exell on 2009-05-03
Hi,
 
I'm attempting to set up a OpenVPN server using Bridge mode on Ununtu and so far I can create the bridge, give it the correct IP settings and give it the IP for it's default gateway. The Unbuntu server appears fine at this point. I can then create my OpenVpn connection and this appears to establish fine. I have set up the VPN to pass all traffic down the VPN and upon connection to the VPN the client is no longer able to see the internet, but this was expected as I have yet to tell Ubuntu how to route the traffic from the bridge. The problem is I can't seem to work out how to do this!
 
Some details:
 
gateway: 10.0.2.2
 
Bridge: br0, 10.0.2.15
 
Ethernet adapter: eth0, no ip due to bridge.
 
VPN Adapter: tap0, no ip due to bridge.
 
Client VPN IP after connect: 10.0.2.50
 
Subnet on all: 255.255.225.0
 
 
from "brcrl show":
 
bridge name...... bridge id..................... STP enabled....... interfaces
br0................... 8000.080027247a53..... no...................... eth0
....................................................................................... tap0
 
 
This appears to show bridge is up as expected.
 
I have added;
 
route add default gw 10.0.2.2 dev br0
 
to ensure that I can continue to see the gateway after bridge is established and added
 
iptables -A INPUT -i tap0 -j ACCEPT
iptables -A INPUT -i br0 -j ACCEPT
iptables -A FORWARD -i br0 -j ACCEPT
 
iptables -t nat -A POSTROUTING -s 10.0.2.0/24 -o br0 -j MASQUERADE
 
after reading a few tutorials in attempt to pass data from client to gateway but to no avail. I'm obviously missing something!
 
I'm rapidly running out of ideas on this - Can anybody help?!

---

