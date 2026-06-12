---
title: "Can't connect nonlocally after 12.10 upgrade"
date: 2012-11-29
forum: Networking &amp; Wireless
---

### Post by pwabrahams on 2012-11-29
I've just upgraded one of my systems from 12.04 to 12.10.  Now I can't connect on that system beyond my local network.  Connections within the local network seem to work fine, and I can make nonlocal connections from other machines (like the one I'm sending this post from).  I suspect that some routing information has been messed up, but I don't know where to look for it.   It's not a nameserver problem -- pinging outside sites by their IP addresses doesn't work either.

I have two laptops side by side, both running Kubuntu 12.10.  On the one that can't connect, **arp** produces no output.  On the other one, it produces> 192.168.0.1              ether   00:23:69:fa:ce:ae   C                     wlan0

On the working machine, the output of **netstat** starts with some **tcp** entries. On the nonworking one, those entries are absent.

---

