---
title: "Wake on lan not working in 11.10"
date: 2011-10-24
forum: Networking &amp; Wireless
---

### Post by mattbrowne on 2011-10-24
Has anyone got wake on lan working in 11.10? I've noticed since upgrading that wol isn't working any more, it has worked on my box before so I know the hardware supports it.

I've checked the /etc/network/interfaces calls /sbin/ethtool -s eth0 wol g pre and post start and the lights stay on my network card when the box is shutdown but it doesn't appear to respond to the magic packet (sent from my router or a device attached to my network).

I've seen hints at this not working in 11.10 but as yet not seen anyone being able to fix it hence the new thread.

If anyone can help it would be much appreciated!

---

### Post by rene06 on 2011-11-02
Any luck with this? I'm having the same problem. Wol was working under winxp. In  ubuntu server 11.10, I can enable wol with ethtool, but when I run halt, I get a message that says something along the lines of Deactivating network. After halt, server is unreachable when pinged, but the light next to the ethernet cable stays on. I also changed the halt script from networkdown=yes to networkdown=no, but it didn't make any difference.

BTW, I have an nVidia MCP2A Ethernet Controller.

---

### Post by legendli on 2011-11-28
I have the same issue in my Dell Precition T3400, this machine can be WOL if I shutdown it by windows or hold the power botton, but can't be WOL if shutdown by Ubuntu server 11.10.

---

### Post by maslokm on 2012-01-12
Look here:
[http://ubuntuforums.org/showthread.php?t=1380776](http://ubuntuforums.org/showthread.php?t=1380776)

You need to manually enable your network card using acpitool.

---

