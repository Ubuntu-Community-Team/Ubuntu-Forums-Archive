---
title: "Strange, wired transfer speeds between Ubuntu and Windows"
date: 2012-04-01
forum: Networking &amp; Wireless
---

### Post by markdavidoff on 2012-04-01
[COLOR="Red"]**Note:** I think the bottleneck is in the router. I found a work-around, but would still appreciate advice. See update below:[/COLOR]

**[SIZE="3"]The Problem:[/SIZE]**

I'm getting very strange and inconsistent file-transfer results in two different situations. I would like someone to help me diagnose my issues.

**[SIZE="3"]The Hardware:[/SIZE]**

**Server:**
[LIST]
[*]Ubuntu desktop 11.04
[*]2TB Samsung HD204UI HDD formatted with ext4
[*]Samba file sharing
[*]ethtool reports a 1000Mb/s connection Full Duplex
[/LIST]

**Desktop**
[LIST]
[*]Windows 7
[*]320GB WD3200AAKS-22SBA0 SATA HDD
[*]Mapped Network drive to the server
[*]100.0 mbps connection in network settings
[/LIST]

**Router:**
[LIST]
[*]Billion 7800N with latest firmware
[*]Everything is wired with Cat 5.e cable (no wireless)
[/LIST]

**[SIZE="3"]The Situations:[/SIZE]**

**Situation 1 - Through the router:**
[LIST]
[*]One large file transfer (not multiple files)
[*]From the Server to the desktop, I can transfer a file at a speed of up to 1.0 MB/s with an average of about 512 KB/s (VERY poor) Using Tera Copy on the Windows Machine
[*]From the Desktop to the server, I can transfer a file at a speed of up to 3.0 MB/s with an average of about 2 MB/S (Quite poor) Using Tera Copy on the Windows Machine
[*]Same results from another desktop machine.
[/LIST]

**Situation 2 - Direct connection from server to desktop via Cat5.e cable:**
[LIST]
[*]One large file transfer (not multiple files)
[*]From the Server to the desktop, I can transfer a file at a speed of up to 16.0 MB/s with an average of about 10 MB/S (Good!) Using Tera Copy on the Windows Machine
[*]From the Desktop to the Server, I can transfer a file at a speed of up to 1.0 MB/s with an average of about 512 KB/s (VERY poor!!??) Using Tera Copy on the Windows Machine
[/LIST]

**[SIZE="3"]Summary:[/SIZE]**
[LIST]
[*]With the router as a go-between both file transfers are poor, with the desktop->server transfer as being faster (but still slow)
[*]With a direct connection the server->desktop is very fast, but the desktop->server transfer is comparable to the server->desktop transfer with the router in-between.
[*]**Note:** The router supports a gigabit connection
[*]**Note:** With a direct connection, ethtool and windows still report the same speeds.
[/LIST]

**Why am I getting such poor and strange results?**

**[SIZE="3"][COLOR="Red"]Update 1:[/COLOR][/SIZE]**
[LIST]
[*]I found that connecting the two computers through a DLINK 10/100 Speed Switch (DES-1008D) results in great transfer speeds between the two computers, comparable to the direct server->desktop speeds (about 10 MB/S).
[*]ethtool reports that my server is connected at 100Mb/s speeds through the switch.
[/LIST]

So, I guess the bottleneck is the router?

I thought a bottleneck could be because of the variation between the desktop and server auto-negotiated connection speeds.
For instance, the desktop seems to only be able to connect at 100Mb/s (even through the router),
but when connecting with a direct connection, the auto-negotiated speed from the server to the desktop was still at 1000 Mb/s (while the Desktop reported 100 Mb/s)
However, changing this manually to 100 Mb/s on the server just made this even slower, so I assume it's an issue with the router, or a configuration issue on a machine.

---

### Post by inobe on 2012-04-01
what about linux to linux?

it'l be interesting to see that situation.

---

