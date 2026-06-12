---
title: "Forcing a particluar application to use wlan0"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by stashu on 2009-02-13
Hello everybody - long-time lurker, first-time poster.

I've tried very hard to find an existing answer for my problem, but with no luck. So I've given in, and have decided to post about it. Here it is -

I have on my machine two interfaces:
[LIST]
[*]eth0 is connected to the 192.168.1 network, with internet access through the 192.168.1.1 gateway.
[*]wlan0 is connected to the 192.168.0 network, with internet access through the 192.168.0.1 gateway.
[/LIST]

What I'd like is for my torrents to **only** utilize wlan0. That is, I'd like any torrent downloading to go through 192.168.0.1 .

My first (probably naive) thought was to mess with the routing table. Unfortunately, I still must be able to access the machine from the internet through 192.168.1.1 , so this won't work.

I was told that I could make an iptables rule for the bittorrent ports, but I've noticed that torrent downloading connections are made to various ports, not just those in a particular range.

If anyone can help, I would appreciate it very much. Here's some info, let me know what else might be needed:

Ubuntu 8.10
torrentflux-b4rt with bittornado backend

Thanks in advance!

---

