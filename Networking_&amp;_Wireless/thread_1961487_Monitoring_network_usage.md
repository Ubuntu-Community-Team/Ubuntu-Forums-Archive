---
title: "Monitoring network usage"
date: 2012-04-19
forum: Networking &amp; Wireless
---

### Post by NRV on 2012-04-19
need help please. i would like to know if there is a command you can execute in terminal which will show:

- the connected users in a LAN & their ip addresses
- bandwidth usage

i'm trying to monitor which ip addresses in a LAN are downloading large files from the internet that causes our connection to slow down. tia :) btw, using ubuntu 11.10.

---

### Post by josephmills on 2012-04-19
> **NRV said:**
> need help please. i would like to know if there is a command you can execute in terminal which will show:

- the connected users in a LAN & their ip addresses
- bandwidth usage

i'm trying to monitor which ip addresses in a LAN are downloading large files from the internet that causes our connection to slow down. tia :) btw, using ubuntu 11.10.

```
apt-cache search bandwidth monitor
ktorrent - BitTorrent client based on the KDE platform
awn-applet-bandwidth-monitor - Display information from network
bmon - portable bandwidth monitor and rate estimator
bwm-ng - small and simple console-based bandwidth monitor
ctorrent - BitTorrent Client written in C++
ibod - ISDN MPPP bandwidth on demand daemon
ifstat - InterFace STATistics Monitoring
ipband - daemon for subnet bandwidth monitoring with reporting via email
iptotal - monitor for IP traffic, not requiring SNMP
libgrapple-1.0-1 - a network layer designed for games
libgrapple-dev - a network layer designed for games (development files)
netams - network traffic accounting and monitoring daemon
netams-dbg - debug symbols for NeTAMS
netams-web - web interface for NeTAMS
nload - realtime console network usage monitor
tor-arm - terminal status monitor for tor
vidalia - controller GUI for Tor
videogen - Create arbitrary-res modelines using hardware parameters

```


take your pick I like bmon just saying it make me feel cool like a rasta man

---

