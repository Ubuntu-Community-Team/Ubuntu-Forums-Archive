---
title: "DHCP server and Router on the same network?"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by pepsifx357 on 2011-02-13
Hey guys, There's this problem that has been bothering me for some time.  I want to create a DHCP server coupled with a DNS server on my network, but I'm not sure how to go about it with my Netgear router on the same network.  My network is basically this:

Modem
  v
Router
  v
switch
   v          v         v         v       v
Computer1 Computer2 Computer3 Computer4 Server

I want the server, which is connected to the switch, to be the DHCP/DNS server and the router to sit back, shut up, and be a firewall.  How can I do that?

---

### Post by perspectoff on 2011-02-13
You should only have one DHCP on the network. Almost every router I've seen allows you to turn off its built-in DHCP server, though. Just hunt around for the settings to turn it off in the router (if you intend to create your own independent DHCP server).

If you plan to have nested networks, of course, the nested network can have its own DHCP server and the "outer" network have its own as well. You just can't have two DHCP server on the same subnet.

For example, I have a network number 10.0.1.1/24. It has its own DHCP server (which is the router's).

Then I have a nested subnet numbered 192.168.0.1/24. The router for that subnet has a static IP address on the "external" network of 10.0.1.254, so that the entire nested subnetwork appears as if it were a single "device" to the "external" network.

However, the nested router has its own DHCP server enabled only for the subnet 192.168.0.1/24 (and not for 10.0.1.1/24).

The devices that connect to this subnetwork router all have IP addresses 192.168.0.100, 192.168.101, etc. 

(I happen to have three nested subnetworks. They don't talk to each other, which is the whole idea. But they share a single Internet connection through the "external" network.)

---

### Post by perspectoff on 2011-02-13
I only have one question. Your network structure appears very simple to me. Why do you want your own DHCP server? I could see having your own DNS server (which I have on my network) if you have a lot of servers and devices on your LAN. 

But a DNS server doesn't have to do DHCP as well. 

Why not leave all the DHCP functions with the router?

---

### Post by pepsifx357 on 2011-02-13
Ok, the nested stuff is a little over my head.  There is an option to turn off DHCP on the router but how would the other computers connect to the internet?

I see....So I guess I should be focusing on a good DNS server then; which is also over my head as far as what I have been reading.

---

### Post by diamondnular on 2012-06-26
> **perspectoff said:**
> You should only have one DHCP on the network. Almost every router I've seen allows you to turn off its built-in DHCP server, though. Just hunt around for the settings to turn it off in the router (if you intend to create your own independent DHCP server).

If you plan to have nested networks, of course, the nested network can have its own DHCP server and the "outer" network have its own as well. You just can't have two DHCP server on the same subnet.

For example, I have a network number 10.0.1.1/24. It has its own DHCP server (which is the router's).

Then I have a nested subnet numbered 192.168.0.1/24. The router for that subnet has a static IP address on the "external" network of 10.0.1.254, so that the entire nested subnetwork appears as if it were a single "device" to the "external" network.

However, the nested router has its own DHCP server enabled only for the subnet 192.168.0.1/24 (and not for 10.0.1.1/24).

The devices that connect to this subnetwork router all have IP addresses 192.168.0.100, 192.168.101, etc. 

(I happen to have three nested subnetworks. They don't talk to each other, which is the whole idea. But they share a single Internet connection through the "external" network.)
Correct me if I am wrong, but as fas as I understand, one can have multiple DHCP on the same network/subnet. When a client connects to the network, it sends out a DHCPREQUEST and the first DHCP receives the request will offer the lease. To avoid conflicts, when setting up two or more DHCP servers, the offering ranges should not overlap to each other.

---

### Post by asmoore82 on 2012-06-26
> **pepsifx357 said:**
> Ok, the nested stuff is a little over my head.  There is an option to turn off DHCP on the router but how would the other computers connect to the internet?

Your router already assigns itself a static IP something like 192.168.1.1. So you'd need to configure the DHCP server to have it's own separate static IP, and to include in its DHCP offers these specifics: nameserver = same as DHCP server, assuming you roll your own DNS; default gateway = same as router box.

---

