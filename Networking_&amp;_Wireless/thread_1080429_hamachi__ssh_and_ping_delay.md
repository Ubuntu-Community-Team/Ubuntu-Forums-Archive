---
title: "hamachi  ssh and ping delay"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by dad311 on 2009-02-25
Has anyone experienced a connection delay with Hamachi and Ubuntu 8.10?  When I try to ssh or ping to another Hamachi machine, I sometimes get a 30-60 second delay.

Ive search around and found some info on editing the hamachi default gateway, but it did not help after making the changes.

Also this only seems to be an issue with remote machines.  Machines connected to the same physical LAN don't seem to have this issue. 

I don't have this issue with Centos and Windows , just Ubuntu.

I used Wireshark to troubleshoot the connection, what I saw was 2-3 ARP requests (request & ack) before a ping would acknowledge.

thx for any help

---

### Post by dad311 on 2009-04-20
After some troubleshooting, this appears to only be an issue with pinging some yahoo DSL accounts via Hamachi.  Dont know why, but it is what it is.:?

---

