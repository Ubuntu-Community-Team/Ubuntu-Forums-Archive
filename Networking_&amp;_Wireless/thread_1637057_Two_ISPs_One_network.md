---
title: "Two ISPs One network"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by ki4jgt on 2010-12-03
If I have 2 ISPs and one computer network. Which ISP is used for the Internet?

---

### Post by jerenept on 2010-12-03
> **ki4jgt said:**
> If I have 2 ISPs and one computer network. Which ISP is used for the Internet?

How do you intend to accomplish this, sir?

---

### Post by ki4jgt on 2010-12-03
Hypothetical question That I've always wondered about (Keep in mind don't plan to do it)

ATT and Satelite internet, or ATT of mine, combined with ATT of neighbors. Create a Neighborhood wifi network where all computers are linked and hence all internet services are shared.

---

### Post by DeadSuperHero on 2010-12-04
Have you tried playing with a DNS cache that theoretically piped packets from one router to another somehow? Then in theory you could possibly pipe services from one to the other, and users could use sort of a "mesh" of both.

---

### Post by ST3ALTHPSYCH0 on 2010-12-04
Businesses frequently do this to insure redundancy of service (the 2 ISPs).... You need a dual WAN Router (or firewall software capable of Dual WAN and a machine with at least 3 NICs [one for each WAN and one for the LAN] also, with only 3 NICs on the firewall you'll need a switch). If you want to use both ISPs simultaneously you'll need a router that offers load balancing (and if you use 2 connections from the same ISP, you'll need a router that offers load balancing for two WAN connections on the same subnet). If you don't get a router with load balancing, the second WAN will only be for fall over (i.e. connections that are dropped by the primary. Basically, it will usually only be used if the primary disconnects.)

---

### Post by jerenept on 2010-12-04
> **DeadSuperHero said:**
> Have you tried playing with a DNS cache that theoretically piped packets from one router to another somehow? Then in theory you could possibly pipe services from one to the other, and users could use sort of a "mesh" of both.

Yeah, Gosalia's DNS Cache could definitely do this.....

[http://gosalia.org/]("http://gosalia.org/")

---

### Post by #11u-max on 2010-12-05
> **jerenept said:**
> Yeah, Gosalia's DNS Cache could definitely do this.....

[http://gosalia.org/](http://gosalia.org/)
what if the intuitive UI is too much for me to handle?

---

