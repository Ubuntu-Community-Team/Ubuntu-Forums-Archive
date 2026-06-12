---
title: "How to allow VPN connections THROUGH an Ubuntu box"
date: 2006-04-11
forum: Networking &amp; Wireless
---

### Post by OfficeLinebacker on 2006-04-11
Hey guys.

I set up dhcp3-server on my machine and basically have it working as a router on my network.  One NIC plugs into the cable modem, the other on goes to a switch.  WOrks great for web surfing and folding@home (only two things that really access the internet).  Oh yeah, updating programs.

Anyway one thing for which it does NOT work *yet* is my work laptop connectivity.

The laptop uses a Cisco VPN client and I get the error "remote peer is no longer responding" but really the signal is never reaching the peer.

I have verified that the lappy is getting an IP via DHCP.  The lappy doesn't allow any kind of outgoing connections except by VPN, so I have no way to tell if it "has a connection" other than by VPN.

Thanks in advance.

---

### Post by OfficeLinebacker on 2006-04-11
bump?

---

### Post by OfficeLinebacker on 2006-04-11
no luck, huh?

---

### Post by changlinn on 2006-04-12
Is this a ipsec cisco connection, you will need to set your ubuntu pc to allow ipsec tunneling... I don't know how to do that, but you can google it.
You have made your ubuntu box into a router, and you need it to support this, ipsec pptp tunneling.

---

### Post by OfficeLinebacker on 2006-04-12
using your advice I found openvpn and simply did sudo apt-get install openvpn and I went to my work computer and voila! it worked!

---

### Post by changlinn on 2006-04-12
I don't see how that worked, openvpn is a vpn server. You have your ubuntu pc setup as a router, installing openvpn on it shouldn't automatically allow ipsec/pptp pass through.. if someone can explain why I'd be very interested.

---

### Post by OfficeLinebacker on 2006-04-13
That's a great point.  Certainly a million monkeys at a million keyboards moment.

---

### Post by happosai on 2006-09-02
I'm not of expert of linux, but I had the same problem.
I solved it just installing shorewall (apt-get install shorewall) and configuring it with webmin.
So u can make an ubuntu box "router" with 
 -ip sharing (echo 1 > /proc/sys/net/ipv4/ip_forward);
 -ip masquerading
 -vpn tunneling
 -firewall

I paste mu configuration files and I hope it would be helpfull
Shorewall configuration files are stored in /etc/shorewall.

#zones
fw	firewall
net	ipv4
loc	ipv4

#masq (i have an ADSL modem)
ppp0    eth0

#interfaces
net	ppp0	detect
loc	eth0	detect
loc	eth1	detect

#policy
loc	net	ACCEPT
loc	fw	ACCEPT
fw	loc	ACCEPT
fw	net	ACCEPT
net	all	DROP	info
all	all	REJECT	info

#tunnels
gre	loc
ipsec	loc

#rules
ACCEPT	net	fw	tcp	80,22,21,110,8080
ACCEPT	net	fw	icmp
ACCEPT	loc	fw	tcp	80,22,21,110,8080
ACCEPT	loc	fw	icmp

Good luck!
Bye!

---

### Post by OfficeLinebacker on 2006-09-02
I'll have to give that a try.  :thumbs:

---

