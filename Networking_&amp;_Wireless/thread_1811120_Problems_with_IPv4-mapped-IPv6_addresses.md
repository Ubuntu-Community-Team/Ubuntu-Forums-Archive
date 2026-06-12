---
title: "Problems with IPv4-mapped-IPv6 addresses"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by Symon_ on 2011-07-24
I'm working with this network architecture.

A machine called "Client"

interface eth0
IPv4 address 50.50.10.2
IPv6 address 2001:123:456:789::10

A machine called "Proxy"

interface eth1
IPv4 address 50.50.10.1
IPv6 address 2001:123:456:789::1

interface eth0
IPv4 address none
IPv6 address 2001:987:654:321::12

A machine called "Server":

interface eth0
IPv4 address none
IPv6 address 2001:987:654:321::2

In the machine called Proxy there's a proxy configured to work in transparent mode.
In the machine called Server there's a very simple server, which takes the request and send a stupid reply.
The communications beetween Proxy and server MUST be in UDP and MUST use IPv6.

Now, if I send a request from Client using IPv6, there are no problems. The request arrives to the proxy, then to the server. A reply leaves from the server, gets through the proxy, and arrives to the client. All in transparent mode.

But if I send a request from Client using IPv4, not everything works. In the proxy there's a mapping from an IPv4 address to the real IPv6 address of Server. So a packet exits from Proxy with source address ::ffff:50.50.10.2 and destination address 2001:987:654:321::2, and arrives to the server, which reads it and starts to write the answer. But the reply is never sent, because the server program crashes with a "Network is unreachable" error. The reply should have source address 2001:987:654:321::2 and destination address ::ffff:50.50.10.2. 
Giving the command

[FONT="Courier New"]ip -6 route show[/FONT]

the result is

[FONT="Courier New"]::ffff:50.50.10.0/120 via 2001:987:654:321::12 dev eth0  metric 1024 
2001:123:456:789::/64 via 2001:987:654:321::12 dev eth0  metric 1024 
2001:987:654:321::/64 dev eth0  proto kernel  metric 256 
fe80::/64 dev eth0  proto kernel  metric 256 
fe80::/64 dev eth4  proto kernel  metric 256 
unreachable fe80::/64 dev lo  proto kernel  metric 256  error -101[/FONT]

so the packet should find its route.

Where am I wrong? Could someone give me an help? Thanks in advance.

---

### Post by lemming465 on 2011-07-27
I think the IPv4-in-IPv6 "mapped" addresses with prefix 0::FFFF/96 aren't legal on the wire and can't be routed as is.  The server would have to have a v4 address and v4 route for 50.50.10.0/24 to reply to ::FFFF:50.50.10.0. See RFC 4038.  Mapped addresses do however show up in log files and are popular in dual-stack API's, as everything can be treated as if it were a v6 address.

The proxy needs to be emitting packets with its real v6 source address of 2001:987:654:321::12 toward the server, regardless of which protocol received the packet on eth1.

---

### Post by Symon_ on 2011-07-31
Thank you for your answer.

I thought to have made some mistake, but now I'm seeing the system is simply following the standards.
Implementing the proxy in the way you proposed is the last resource, because in this way transparency isn't fully implemented on the server side. I will try to find other ways before.

Thank you again.

---

