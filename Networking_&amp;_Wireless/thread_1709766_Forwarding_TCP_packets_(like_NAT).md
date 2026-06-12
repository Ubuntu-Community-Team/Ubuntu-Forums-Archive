---
title: "Forwarding TCP packets (like NAT)"
date: 2011-03-18
forum: Networking &amp; Wireless
---

### Post by Frank9321 on 2011-03-18
Hi,
first of all, I would like to apologize for my bad English as I am French. So please excuse me for all my mistakes.

This is where it starts:
I have 2 networks.
The  first: 192.168.1.0/24 composed by the router which has access to the  internet with the IP 192.168.1 and the server (who is a gateway) with  the IP 192.168.1.42
The other network: 192.168.2.0/24 composed by the  gateway with the IP 192.168.2.1 and the clients (on the 192.168.2.0/24  subnet).

To sum up, the gateway has 2 IPs (192.168.1.4(eth0) and  192.168.2.1(eth1)). On this gateway, I have squid installed (and  listening on port 3128 ). I also made a redirection to redirect some  computers who want to access to the web (port 80) to squid (port 3128 )  with this command:[FONT=Verdana]
[/FONT]_/sbin/iptables -t nat -A PREROUTING -m mac --mac-source CLIENT_MAC -p tcp -m tcp --dport 80 -j REDIRECT --to-port 3128_

At this stage, everything works fine. The clients can access the web by the proxy without "knowing".
What I wanted to do, is redirect also the port 443 (HTTPS).
Actually, when a client wants to access to, for example, [https://gmail.com]("https://gmail.com/"). He cannot.
So I would want to be able to redirect people (without passing by any proxy) directly to google. Like a NAT.
But the problem is that I can't.
The  thing would be to, in the gateway, take all the packets with port 443  in destination and handle them to the router 192.168.1.1. Then, when the  router sends the packet back, the gateway takes the packet and handles  it to the client.

I tried putting ip_forward to 1, but the problem is that all IPs and **ALL PORTS** are forwarded. And I just want port 443 to be forwarded.

Do you have any solutions ?

Many thanks in advance !

Cheerfully !

Frank

---

