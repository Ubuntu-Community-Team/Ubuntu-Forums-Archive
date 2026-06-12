---
title: "Weird issue. I can SSH to and from the box, but aside from that the net's unreachable"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by kaldor on 2010-08-19
This is on Ubuntu 10.04 Server Edition.

The ethernet cord was disconnected one day. I plugged it back in to find I can ssh to and from that machine, but I cannot update or browse the web (elinks) on it. I tried "ifconfig eth0 up" which did nothing.

Why is it that only local connections work?

---

### Post by beren.olvar on 2010-08-19
if when you are connecting through ssh you are using directly the ip addresses, then the problem is probably the dns configuration.

For example, try directing your browser to 173.194.37.104 that should take you to google.

Since I don't know your network configuration, I don't know hot to solve the problem, but if you have the network manager applet installed, should be easy to check your DNS configurations.

---

