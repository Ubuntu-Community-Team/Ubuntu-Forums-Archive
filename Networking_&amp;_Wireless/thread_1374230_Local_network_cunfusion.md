---
title: "Local network cunfusion"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by jaxinabox on 2010-01-06
[CENTER]:confused:[/CENTER]
I have a ubuntu 9.04 machine i'm using as a file server. I'm able to see that machine from any XP machine, connect to it's shares play music, movies, work off of it NO problems. But i can't view the shares from a windows 7 home edition PC (garbage). AND, from the ubuntu PC, i can't see any of the other shares on network. I get "Fail to receive share list from server". 

**NOTE**: Originally i had this machine connected with wireless card because of location. and I was able to see all shares then - both ways (still not from Windows 7 PCs though). However, when I moved to hard wire connection, the network disappeared. I've tried changing IP addresses, changing switches, but no network. I'd like to keep it hard wire.
Can anyone point me in right direction or am i missing information? Thanks in advance

---

### Post by gordintoronto on 2010-01-06
Firewalls often block file-sharing connections.  All the computers are behind a router, so a firewall does very little for them.

Are all the computers set to the same workgroup?  You should be able to begin at Places/Network, then double-click your way through Windows Network, the workgroup, a computer, a share on that computer.

---

