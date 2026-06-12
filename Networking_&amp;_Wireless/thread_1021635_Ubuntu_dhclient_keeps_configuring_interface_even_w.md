---
title: "Ubuntu dhclient keeps configuring interface even when &quot;static&quot; cofigured"
date: 2008-12-25
forum: Networking &amp; Wireless
---

### Post by InuY4sha on 2008-12-25
Hi all,
I'm having troubles with dhclient process in U8.10 ... I've got 2 interfaces which I want to configure with STATIC ips; for some reason the "static" keyword used in /etc/network/interfaces does not seem to affect the behavior when starting the interface up. The result is that the interface sends a DHCP request to the other side of the LAN cable and gets a reply from the server. The reply shadows my settings and configures the IP of the iface, the ROUTING TABLE DEFAULT GATEWAY [adding a new one] and the /etc/resolv.conf file setting a new DNS.

You could be wondering WHY I've got a DHCP server providing wrong info and so on.. basically I appreciate the work of the DHCP server and I could need it in future. Currently I do not, therefore I want to keep the server running for future usage, while having my laptop connect with a STATIC IP and without updating any information about the network routing & dns.
I can post the current /etc/network/interfaces file content:

auto lo
iface lo inet loopback

#This one goes to internet
auto eth1
iface eth1 inet static
	address 192.168.0.3
	netmask 255.255.255.0
	gateway 192.168.0.1
	wpa-driver wext
	wpa-conf /etc/wpa_supplicant.conf
#When this (eth0) is brought up, it shadows the prev. settings 
#with the received DHCP reply.
auto eth0
iface eth0 inet static
	address 192.168.2.2 #Here this is not kept
	netmask 255.255.255.0

Note that I tried this kind of tricks... 
	post-up sleep 1
	post-up echo "nameserver 192.168.1.1" > /etc/resolv.conf
but they are a bad workaround that could miserably fail in case the DHCP reply takes more that 1 second.
I'm wondering why the "static" suffix is not preventing the dhclient from spamming around with DHCP requests...Maybe I'm not really understanding the meaning of it... 
Thanks in advance!

---

### Post by Iowan on 2008-12-26
> **InuY4sha said:**
> I'm wondering why the "static" suffix is not preventing the dhclient from spamming around with DHCP requests...Maybe I'm not really understanding the meaning of it... 
Thanks in advance!I've seen that happen before.  NM apparently has some "interesting" attributes. There is a [workaround]("http://ubuntuforums.org/showthread.php?t=974382").  Another thread suggests removing the "auto eth0" line.  Yet another mentions removing dhclient (or disabling it).

---

