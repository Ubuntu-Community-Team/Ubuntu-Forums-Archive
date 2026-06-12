---
title: "Can send but not receive wireless packets"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by eee1000huser on 2009-02-09
Hi,

I've set up my atheros 5007 wifi card as an access point using madwifi driver. I can see this access point being advertised and I can connect to it from another laptop.

The strange behaviour I'm getting is that it can send data (e.g. ping) fine, but it never receives any packets.

I checked using athdebug and can see that packets actually arrive in the kernel.

I dont think its firewall problem since I cleared iptables and set it to accept everything.

Has anyone come accross behaviour like this?

Btw: I'm using ubuntu 8.10, on eee pc 1000H, with a new wireless card gigabyte aircruiser 5007.

---

### Post by Sam Lars on 2009-02-09
Does the ping command tell you 0% of packets were received?

---

### Post by eee1000huser on 2009-02-09
yes ping tells me 0% received.... 100% packet loss

---

