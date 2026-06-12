---
title: "OpenVPN works on TCP but not UDP (network-manager-openvpn)"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by amaurynieto on 2010-02-03
Hello friends - been an avid and nonstop user of Ubuntu since late 2006 - been a VPN user for over a year now.

I was first using OpenVPN through KVPNC, however noticed that it would be easier to use the network-manager plugin. 

Since I upgraded to 9.04, and then 9.10, I've only been able to route my traffic when using a TCP port, not UDP.

What I mean by that is, on BOTH TCP and UDP, the connection is successful, the little lock enables and the tunnel is established.

The only difference is, that TCP does route traffic to my computer properly and I can display webpages, and any and all services, while UDP, while established, IP given, and everything, does NOT route any traffic.

I'm thinking IPTABLES issue.

I've already tried this: which comes from the openvpn.net faq:

# Allow TUN interface connections to OpenVPN serveriptables -A INPUT -i tun+ -j ACCEPT

 # Allow TUN interface connections to be forwarded through other interfacesiptables -A FORWARD -i tun+ -j ACCEPT

# Allow TAP interface connections to OpenVPN serveriptables -A INPUT -i tap+ -j ACCEPT

 # Allow TAP interface connections to be forwarded through other interfacesiptables -A FORWARD -i tap+ -j ACCEPT

It also says one should enable IP forwarding. but my big beef with this is, it is working with TCP, it makes no sense to me that it won't route traffic properly through UDP.

I would like to switch back to UDP, since I have better bandwidth usage and less throttling from my ISP.

As far as the obvious checklist of items to check:

a) Yes, the port I am using is forwarded, furthermore, it's in DMZ mode

b) It works on UDP mode on the same computer both on a dd-wrt router with openvpn (big), using the same modem gateway

c) It works on the same computer using Windoze OpenVPN on Win XP.

I have been reading around and found that it's a common error and that iptables have to be edited in order to make it work - I unfortunately have tried both the FAQ on the OpenVPN site, as well as numerous other posts I've read around on, to no avail.

A support person from my VPN provider even suggested (I didn't really try his solution) that i should disable iptables entirely. I don't think this is even possible, or even if it's a good idea.

If you might lend a hand I would be very grateful - if you need me to post any logs at all, I will most gladly do so.

---

