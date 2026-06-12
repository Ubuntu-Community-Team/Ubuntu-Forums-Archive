---
title: "Only use vpn for torrent traffic"
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by SpinningAround on 2011-08-08
I'm trying to configure iptables in such a way that torrent traffic only go by the vpn. Problem is that new connections get stuck at SYN_SENT (netstat -t), the strange thing is that ssh, http, https work fine. It's only torrent traffic that cause problem, I would guess that it has something to do with using tap0 as in and out interface, or could it be something else?

Since I'm a beginner with iptables is advice welcome.

EDIT: Removed parts that I think would not be relevant.

EDIT 2: I'm using deluge might that be the cause, that the program uses eth0 (standard) but it's only allowed to use tap0.

EDIT 3: (Solution)
Finally got it working by using the same port span for outgoing and incoming connection, question is why.

---

