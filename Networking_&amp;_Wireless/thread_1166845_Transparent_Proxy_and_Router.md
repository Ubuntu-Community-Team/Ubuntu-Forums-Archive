---
title: "Transparent Proxy and Router?"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by jamestech on 2009-05-22
OK, I may be asking the impossible here but I am pretty damn stubborn, I have a small network for a PC repair business, I would like to setup a transparent proxy server running Ubuntu 9.04, so far our connection comes in as follows...

[INDENT]
ADSL Router:
IP: 192.168.3.1

---wired to---

DD-WRT Router WAN:
IP: 192.168.3.254
Subnet: 255.255.255.0
Gateway: 192.168.3.1
DNS: 208.67.222.222 (OpenDNS)

DD-WRT Router LAN
IP:192.168.1.1
Subnet: 255.255.255.0
[/INDENT]

This works perfect at the minute however I would like to add a machine as a transparent proxy as follows...

[INDENT]
ADSL Router:
IP: 192.168.3.1

---wired to---

UbuntuPC WAN:
IP: 192.168.3.254
Subnet: 255.255.255.0
Gateway: 192.168.3.1
DNS: 208.67.222.222 (OpenDNS)

UbuntuPC LAN:
IP: 192.168.2.1
Subnet: 255.255.255.0

---wired to---

DD-WRT Router WAN:
IP: 192.168.2.254
Subnet: 255.255.255.0
Gateway: 192.168.2.1
DNS: 208.67.222.222 (OpenDNS)

DDWRT Router LAN:
IP:192.168.1.1
Subnet: 255.255.255.0
[/INDENT]

First of all is this possible, secondly is there a guide anywhere to point me in the right direction, I have tried [here]("http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html") and [here]("http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html") but there are always differences in their setup and mine that I don't understand (particularly in the squid.conf) plus I am not sure these will do my routing?

Can anyone help?

---

### Post by helgman on 2009-05-22
I'm pretty sure this can be done.

As for the routing, that's the "easy" part (look for "Enable Routing" [here]("https://help.ubuntu.com/community/Internet/ConnectionSharing")). As for the proxy, I'd make sure that routing is working first and then move on to the proxy ...

Regards,
Helgman

---

