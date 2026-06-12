---
title: "Verizon Wireless Router - ppp0 disconnects"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by agent000 on 2010-05-15
I've setup Ubuntu 10.04 server as a 3G router with a Verizon UMW190 USB adapter. I am able to connect but ppp0 disconnects as soon as I attempt to connect with another computer.  I've read that Verizon kicks all connections if private network traffic is disconnected, am I missing a config via iptables?

I've tried iptables -I OUTPUT -o eth0 -s 192.168.7.0/24 with no success...

---

### Post by micseydel on 2010-06-26
I'm having a similar problem.

When my Ubuntu 10.04 desktop connects to my Verizon wireless router, the connection is reset on all devices. Then I have intermittent issues after that, every 20-24 minutes.

---

