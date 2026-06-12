---
title: "How do I get my Server to Route?"
date: 2012-06-15
forum: Networking &amp; Wireless
---

### Post by DonThompson on 2012-06-15
I have two in-house networks, 10.1.1.0 and 192.168.0.0 with a Ubuntu 12.04 server straddling them both, wired to the 10.1.1.0 and wireless to the 192.168.0.0.  I would like the server to route traffic between the two networks.  I have two problems:

1) On reboot the wireless card does not come up, but it does start later with sudo ifconfig wlan0 up

2) From the 10... network I can ping the server and its 192.168... network card but NOT through the server.  But from the server itself (after manually starting the wlan0 card) devices both networks can be pinged.

I would think it would be relatively simple to forwardm but it doesn't happen.

The interfaces file is:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# start 'em all
auto lo eth0 wlan0

# The loopback network interface
iface lo inet loopback

# The primary network interface
iface eth0 inet static
	address 10.1.1.8
	netmask 255.255.255.0
	network 10.1.1.0
#	post-up iptables-restore < /etc/iptables.up.rules
	gateway 10.1.1.250
	up ip route add 10.1.1.0/24 dev eth0

# link to Kirstin
iface wlan0 inet static
	address 192.168.0.200
	netmask 255.255.255.0
	broadcast 192.168.0.255
	network 192.168.0.0
	wpa-ssid "[the ssid]"
	wpa-psk [the key]
	up ip route add 192.168.0.0/24 dev wlan0

# 


Removing the comment tag from the post-up line does not help.

Any assistance would be appreciated.

---

### Post by sanderj on 2012-06-15
In /etc/sysctl.conf uncomment this ip forward line:


```
# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

```

Maybe you then have to restart your networking or even your linux system to get it activated.

HTH

---

### Post by DonThompson on 2012-06-15
Thanks for the quick reply.  Sadly, that had already been done.

---

### Post by DonThompson on 2012-06-15
Now wlan0 does not seem to want to work regularly.  Are there serious issues with this (12.04) release or am I just losing it?  I have not had this much trouble with an OS in 10 years.

---

