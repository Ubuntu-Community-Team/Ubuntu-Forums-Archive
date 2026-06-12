---
title: "UFW blocking certain requests and not sure why"
date: 2013-03-18
forum: Networking &amp; Wireless
---

### Post by sirgad on 2013-03-18
Hi,

I'm a firewall beginner, so please be kind.

I'm running UFW (Uncomplicated/Ubuntu FireWall) on a computer acting as a Privoxy server for my LAN and have set it up as follows (only the relevant info is given):

```
ufw allow from <my network range>/28 to any app Privoxy

```
"Privoxy" is defined as follows:

```
[Privoxy]
title=Privoxy, a filtering proxy server
description=Privoxy is a free and open-source ad- and cookie-blocking proxy.
ports=8118

```

I've just inspected my syslog, and noticed a large number of [UFW BLOCK] entries (ie. over 50) in a space of 6 hours or so, of the following type:
```
[UFW BLOCK] IN=eth0 OUT= MAC=<REDACTED> SRC=<REDACTED> DST=<REDACTED> LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=37797 DF PROTO=TCP SPT=60505 DPT=8118 WINDOW=8192 RES=0x00 ACK FIN URGP=0
```
The Source Port changes, but only between 598xx - 60xxx.

I've determined that the Source IP address is one of my devices, and that I was probably using it to listen to a BBC iPlayer radio show at the time.  The Source IP address lies within the range permitted by the Firewall rule.  The Destination IP address and port is Privoxy, so nothing untoward there.

So, why is UFW blocking these incoming requests?  If the Source IP Address, Destination Port and Destination IP Address are all valid, shouldn't UFW let these requests through?

---

