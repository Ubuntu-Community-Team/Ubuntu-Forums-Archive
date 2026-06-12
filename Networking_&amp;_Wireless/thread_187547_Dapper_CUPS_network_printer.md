---
title: "Dapper CUPS: network printer"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by shakespeare on 2006-06-03
I have a network printer (HP 7410) which worked fine with CUPS and HPLIP on Breezy. It cannot be found by CUPS on Dapper, but is found by the other PCs on the network.

Dapper PC is 192.168.2.100
Printer is 192.168.2.101

I have Browsing On in browse.conf, Listen localhost:631 in ports.conf, and Detect LAN Printers is on in gnome-cups-manager. Note that putting ServerName 192.168.2.101 in client.conf (as suggested in [Krazy Penguin's Dapper Guide]("http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide")) results in cupsd failing to start, without issuing any error messages.

What do I need in cupsd.conf, client.conf, browse.conf, and ports.conf for this apparently simple setup?

---

### Post by altonbr on 2007-01-29
I second this question.

---

### Post by dsimpson on 2007-01-29
I am the third on that request, this should be a prime area to work on a fix. Where are all the Ubuntu experts on this one?

---

