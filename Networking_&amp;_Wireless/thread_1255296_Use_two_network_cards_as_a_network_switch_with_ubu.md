---
title: "Use two network cards as a network switch with ubuntu server"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by hugo_laffez on 2009-09-01
Hi Everybody,

I am wondering if an Ubuntu server with two network cards can perform the same as a network switch.

My situation is the following: my ISP supplies me with a router which works as a DHCP server and WLAN access point. Unfortunately it has only a single ethernet-port, while I want to connect both my Ubuntu server and another computer via ethernet.

Usually one would use a switch in such a case. I don't have a switch, but I have however an extra pci network card. Therefore I wonder if I could use that instead to get the same functionality (and lower power consumption :)) See the figures below.
[HTML]
With a switch:
+--------+          +--------+          +--------+
| Router |<-------->|        |<-------->| Server | 
| (DHCP) |          |        |          +--------+
+--------+          | Switch |
                    |        |          +----------+
                    |        |<-------->| Computer | 
                    +--------+          +----------+

With an extra network card in the server?
+--------+          +--------+          +----------+
| Router |<-------->| Server |<-------->| Computer | 
| (DHCP) |          +--------+          +----------+
+--------+          
[/HTML]
I get the feeling that I have to bridge eth0 and eth1 in the server, but I have no idea how to proceed from there or how to do it.```

```

---

