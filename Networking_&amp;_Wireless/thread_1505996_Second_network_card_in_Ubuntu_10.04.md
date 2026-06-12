---
title: "Second network card in Ubuntu 10.04"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by bill-linux on 2010-06-09
I'm building a server which needs two ethernet ports on it. I have tried using both a DELL GX270 and a ThinkCentre (8171 WHB) and get the exact same result:

1. The computer (ether one) has a build in NIC (network card) and PCI slots.
2. When I put any 3Com card in the PCI slot (e.g, 3c905tx) it will show up in "lspci" (see below), but will never show a connection with mii-tool ("no link")

This isn't my first spin around the linux block, over the years I've build a number of servers like this ... in face one is operating in my basement. I've tried different NICs, different computer ... and Knoppix, Debian Lenny, and Ubuntu 10.0.4. I've tried modprobe 3c59x, rmmod 3c59x, then reinstalling. In the past I've used 3com cards because they are very linux friendly ... what am I missing here? Has something changed since my last server that I'm just not getting.

lspci shows (for the non-working card):

0a:09:0 Ethernet controler: 3Com Corporation 3c905C-TX/T-M [Tornado] (rev 30)

---

### Post by kalai on 2011-02-22
hai
i am very very new to linux
i installed UBUNTU 9.10
i havnt connected the internet
can anybody tell the step by step procedure to connect net?
i have broadband service at home..!!

---

