---
title: "radvd - forward advertisements on wireless network"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by AGtheKiLLER on 2011-06-16
Hi all,

I have a CBVG834G Netgear router, acting as an IPv4 *modem* for my LAN.
I have a *laptop* with no screen, acting as an IPv6 router for my LAN, sending advertisements for my IPv6 subnet on eth0. It is using a 6in4 tunnel from SixXS.
The laptop and the modem are connected with an Ethernet cable. All computers connected to the Ethernet network are able to autoconfigure an IPv6 address correctly.

My problem is that the IPv6 advertisements are not forwarded on the Wifi network by the Netgear modem. Computers connected to the Wifi network do not receive an IPv6 address. They can still connect to others computers and the laptop, but using IPv4 or link-local IPv6 addresses.

Do you know any way to make the modem forward these advertisements to the Wifi network ? Do I have to tweak the modem's settings, or maybe change something in radvd.conf that will make the advertisements forwardable ?

Thanks for your help.

---

### Post by AGtheKiLLER on 2011-06-17
bump

---

### Post by ratcheer on 2011-06-17
IMHO, the only way to do that will be to make the router the tunnel endpoint and run radvd on the router. That is how I do it with my Netgear WNDR3300. I will check right now to make sure it is doing what I think it is doing (I usually only use the wired ethernet connection).

Tim

---

### Post by ratcheer on 2011-06-17
Maybe I spoke too soon. My wired address is getting an IPv6 assignment on my routed 64, but my wireless connection only has an ipv6 link local address. I'll have to do more checking and get back to you.

Thanks for asking your question. You learn something new every day.

Tim

---

### Post by AGtheKiLLER on 2011-06-19
You are much welcome :)

I'm not sure if I can customize the cvbg834g enough to make radvd run directly inside, but that would be very convenient.

There are two other solutions that I thought of, which I'll try later but are quite ugly:

1) set the cvbg834g to *bridge* mode and use the laptop as an IPv4 & IPv6 router for both the wired and wireless networks. But that involves using a hub for the wired network, and I'm pretty sure the embedded wireless card in the laptop will not be powerful enough to be used as an access point for the whole wireless network...

2) make the laptop connect to the router on the Wifi network as well as the Wired network, and set radvd to send advertisements on eth0 AND wlan0. But I'm not sure what kind of duplicate configs and network loops that would induce. And if the laptop disconnects from the wireless network, IPv6 connection will be lost for all computers on the wireless network...

Thanks for looking for an answer.

---

### Post by ratcheer on 2011-06-21
I posted the question at tunnelbroker.net forum. The last time I looked, no one had responded. I guess I will have to post it in dd-wrt forum, but that is a really tough crowd.

I am still looking, too. I suspect it has something to do with setting up a virtual LAN.

Tim

---

### Post by ratcheer on 2011-07-05
Latest info: I still cant use IPv6 over wireless, but I installed Wireshark and have verified that my wireless interface ***is*** receiving the IPv6 advertisements from the router. So, that is not the problem.

I'm still investigating for a full solution.

Tim

---

### Post by fknaesel on 2013-01-22
Hello all, I would like to know if you could overcome this problem, and if yes, can you give me a hint on how to solve it?
Thanks in advance, Frank.

---

### Post by lemming465 on 2013-01-24
Solving this probably requires a firmware upgrade for proper dual IPv4 + IPv6 stack support on the wireless router, which might require replacing it entirely.

ICMPv6 router advertisements are link-local in IPv6; they are never forwarded across router hops.  In fact, the only way to find the address of your IPv6 gateways is from the fe80:://64 link-local sending address of the RA's; the gateway address is not an option in the RA payload nor even anywhere in DHCPv6.  We're still debating whether this is a bug or a feature of IPv6 :-(

So your router either has to run in bridge mode, or actually support IPv6.

A "standard" solution to islands of v6 forwarding in the midst of a v4-mostly non-dual stack routed LAN network is ISATAP tunneling.  You need a DNS answer for queries of *ISATAP.your.domain.here*, where-upon ISATAP-aware operating systems such as Windows-7, or optionally Linux, seeing no native v6 RA's, but resolving a DNS answer, will use protocol 41 IP-in IP tunneling to the ISATAP router.

---

