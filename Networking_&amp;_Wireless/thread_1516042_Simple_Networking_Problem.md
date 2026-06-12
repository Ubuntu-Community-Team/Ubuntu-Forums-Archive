---
title: "Simple Networking Problem"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by WebCaesar on 2010-06-23
Hello,  I have 2 laptops connected by a lan cable - from 1 laptop network card to the other.  the first laptop is an Asus eeePc that runs a modified version of debian.  this one is connected to the internet and i simply want the other one to connect to the internet via the lan cable.  --------------------------------------------------  the "server" has 2 connections: 1. one for connecting to the internet via a dialup mobile connection (i checked and this connection is shared)  2. the 2nd connection: "Local Area Connection" defined this way: IP address: 192.168.0.4 subnet mask: 255.255.255.0 + it is also marked as 'shared' that's all, no Gateway/DNS/Wins defined  --------------------------------------------------  the "client" (Debian 5.0 Lenny) has its own "Wired connection" defined this way:   Configuration: Static IP address ip addreess: 192.168.0.3 subnet mask: 255.255.255.0 Gateway: 192.168.0.4  -------------------------------------------------- my problem is that the client (192.168.0.3) cannot open web pages even if it sees just fine the server's files.  please let me know what can i do to fix this.  thanks, Andy

---

