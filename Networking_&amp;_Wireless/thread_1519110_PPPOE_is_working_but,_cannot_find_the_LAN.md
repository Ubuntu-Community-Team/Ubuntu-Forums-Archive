---
title: "PPPOE is working but, cannot find the LAN"
date: 2010-06-27
forum: Networking &amp; Wireless
---

### Post by status001 on 2010-06-27
I'm using Ubuntu 10.04. I've a pppoe connection and configured it with NMapplet. My problem is I cannot find any PC on windows network. When I double click on "Windows Network" it says "**Unable to mount location**, Failed to retrieve share list from server". 

I have two lan cards, one of them with connected with the cable. My system detects this connected card as eth0, and the other as eth1. In NMapplet, in "*Wired*" tab, I cannot see eth0, but the eth1 is there.

In terminal running the command "*ifconfig*" returns some inet6 addresses with eth0. No ip like 192.168.X.X or 169.254.X.X.

Also I configured my net connection using the command "*sudo pppoeconf*". That does not help either. The problem still the same.

---

### Post by status001 on 2010-07-10
Anybody there?

---

