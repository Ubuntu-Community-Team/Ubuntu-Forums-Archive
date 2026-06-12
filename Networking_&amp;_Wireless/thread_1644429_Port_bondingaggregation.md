---
title: "Port bonding/aggregation"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by WA1DH on 2010-12-13
I've been reading about using more than one NIC on a server and client PC for port bonding. My gigabit switch does not support LACP. I was wondering if it would be possible to connect something in a setup like this:

Server NIC#1 ----- Switch ----- Client NIC #1
Server NIC#2 ------------------- Client NIC #2

Note that Server NIC 1+2 are on the same PC, and Client NIC 1+2 are on the same PC.

Packets would be sent over the switch on the first link, and direct over a crossover cable on the second. This would create 2x the bandwidth (2 gigabit vs. 1 gigabit). I would imagine this would increase ping time somewhat. Is this a workable configuration?

I have no need for a setup like this right now, but I'm just curious as a possible future upgrade to increase LAN speed.

Thanks.

---

