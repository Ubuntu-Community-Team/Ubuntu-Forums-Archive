---
title: "Disable FW"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by pipboy2000 on 2006-06-09
Hi 

I'm want to be acessible form internet (bittorent network). If I use windows thet everithing is OK port is open, but on linux I have not. I test it on this page ```
http://www.utorrent.com/testport.php?port=666
```.
How I can disable firewall?
I'm using dsl router with FW and i supose to theat one firewall is enough. 
(router is configured to port forwarding.)

Thanks.

---

### Post by jvl on 2006-06-21
Port 666 is under 1024, which is reserverved for root. So unless your torrent client is running as root (pretty bad idea (TM)), it won't work. Forward another port, above 1024 (for example 6666/tcp) and reconfigure your linux and windows torrent clients. AFAIK, ubuntu has no packet filtering enabled by default, so this is not an firewall issue at all.

---

