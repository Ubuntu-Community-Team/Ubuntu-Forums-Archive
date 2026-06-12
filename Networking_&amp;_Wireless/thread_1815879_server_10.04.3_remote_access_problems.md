---
title: "server 10.04.3 remote access problems"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by wmakasa on 2011-08-01
Hi,

I have a server which was updated from 10.04.2 to 10.04.3.  Before this, I was able to access my server remotely through a vpn by both ssh and vnc.  However after the upgrade, i can only do this when on the Local Area Network (LAN) and not remotely.  I can access other servers by ssh and vnc but not the updated ubuntu 10.04.03 server.  I tried to flush iptables and nat tables with no luck until i eventually unistalled iptables, then i was able to vnc into the server but still not ssh.  I suspect that iptables may be buggy on 10.04.03 (as the other linux server and other un-updated ubuntu servers can be accessed remotely).

Anyone with suggestions? :confused:

---

