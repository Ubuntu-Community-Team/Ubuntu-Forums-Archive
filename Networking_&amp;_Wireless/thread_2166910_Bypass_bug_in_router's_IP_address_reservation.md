---
title: "Bypass bug in router's IP address reservation"
date: 2013-08-11
forum: Networking &amp; Wireless
---

### Post by oz1cz on 2013-08-11
[COLOR=#000000][FONT=Arial]I have an laptop running Ubuntu connected to my home network. My home network connects to the outside world through a NETGEAR CG3000 gateway that acts as a DHCP server.

My laptop normally uses a wired connection, and for practical reasons I have set up a fixed IP address reservation for my computer (192.168.1.11) in the router. This works fine, until I carry my laptop to another location in my home and connect to the router through a wireless connection (which gets another IP address). This often (but not always!) causes the router to delete the IP address reservation for my wired connection.

I presume that this is a bug in the router, and I presume that this occurs because the router sees the same hostname on two different MAC addresses. (But I could, of course, be wrong on both counts.)  My question is what can I do on my Ubuntu laptop to solve this?

I do not want to set up a fixed IP address in the laptop because I occasionally need to connect it to other networks where the address 192.168.1.11 may not be appropriate.

Is there any way I can configure my laptop to use a fixed IP address when on my home network and a DHCP-assigned address when on a foreign network?
Alternatively, is there any way I can make the laptop present a different hostname to the DHCP server, depending on whether I connect through the wired or the wireless interface?
[/FONT][/COLOR]

---

