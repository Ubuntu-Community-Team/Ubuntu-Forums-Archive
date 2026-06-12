---
title: "Wireless and Cable Connection same time"
date: 2010-04-07
forum: Networking &amp; Wireless
---

### Post by guta on 2010-04-07
:confused:I need help for this solution:confused:

I have a wireless connection with static ip 192.168.10.150 to connect to Internet through a modem / router ADSL ip Lan 192.168.10.1. I connect with no problems.
I have a wired network in the office 172.16.17.0/24 to work with the servers. the router is 172.16.17.1, my connection eth0 with static ip 172.16.17.150 work, but Internet by Internet *nothing*.
If i disconnect the cable i have Internet from wireless.
?? What i have to do to ,to received internet by wireless and be connected ate same time to my wired network by eth0 too.

all routers have DHCP active.

:lolflag:Tanks in advance

---

### Post by wfarr_09 on 2010-04-07
> guta's post. 
:confused:I need help for this solution:confused:

I have a wireless connection with static ip 192.168.10.150 to connect to Internet through a modem / router ADSL ip Lan 192.168.10.1. I connect with no problems.
I have a wired network in the office 172.16.17.0/24 to work with the servers. the router is 172.16.17.1, my connection eth0 with static ip 172.16.17.150 work, but Internet by Internet *nothing*.

Here's the thing...*YOU CAN'T GO ON WIRELESS & WIRED NETWORKS AT THE SAME TIME!!!!!*

---

### Post by Iowan on 2010-04-07
> **wfarr_09 said:**
> Here's the thing...*YOU CAN'T GO ON WIRELESS & WIRED NETWORKS AT THE SAME TIME!!!!!*Well... it's more complicated than it used to be. */etc/network/interfaces* used to work - Network Manager doesn't play as nice as it did. I've seen some threads that recommend removing NM and using */etc/network/interfaces*, but I've also seen some that lost internet connection when they removed NM.

---

