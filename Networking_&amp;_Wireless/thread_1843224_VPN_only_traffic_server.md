---
title: "VPN only traffic server"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by Pontifex_Maximus on 2011-09-13
The point of the server is that ALL traffic sent by / through (e.g. acting as a gateway, future revision) the server should traverse the VPN and drop all traffic that would normally not be routed through the VPN; E.g. If the VPN connection drops the firewall should drop all traffic sent "in the clear" until the VPN comes back up.

So, configuring my firewall and routing, I wanted to check my work now that I've got a working solution:

NOTE: Using PPTP here until I can convert over to OpenVPN, firewall rules reflect this.

```

me@myserver# route

default * 0.0.0.0 U 0 0 0 ppp0
default 192.168.0.1 0.0.0.0 UG 0 0 0 eth0

me@myserver# iptables -S

-P INPUT DROP
-P FORWARD ACCEPT
-P OUTPUT DROP
-A INPUT -i lo -j ACCEPT 
**SNIP**
-A INPUT -p tcp -m tcp --dport 1723 -j ACCEPT 
-A INPUT -p gre -j ACCEPT 
-A INPUT -s 192.168.0.0/24 -i eth0 -j ACCEPT 
-A OUTPUT -p tcp -m tcp --dport 1723 -j ACCEPT 
-A OUTPUT -p gre -j ACCEPT 
-A OUTPUT -d 192.168.0.0/24 -o eth0 -j ACCEPT 
-A OUTPUT -o ppp0 -j ACCEPT 

```

You'll note I want my local network to be able to be accessible by / to the server, this allows me to use my network shares, etc.

I could make this more secure by configuring an acceptable IP range to accept VPN traffic / connection attempts from.  Next revision.

The routing table is automatically configured to revert to routing all information via eth0 should the ppp0 interface become disabled (e.g. PPTP connection is disconnected) via external scripting.  Tested and working at this time.

Some simple testing shows that this does work as I expect:
[LIST]
[*]pings stop if the VPN goes down and continue only when the VPN connection comes up
[*]normal downloads (e.g. WGET) behave normally when the VPN connection is enabled, fail if it isn't
[*]Etc
[/LIST]

I am by no means a designer of firewalls nor knowledgeable of advanced networking concepts, so if there's something to revise please let me know!

Thank you.

---

