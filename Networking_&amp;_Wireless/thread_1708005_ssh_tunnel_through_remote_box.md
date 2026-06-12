---
title: "ssh tunnel through remote box"
date: 2011-03-16
forum: Networking &amp; Wireless
---

### Post by wlck on 2011-03-16
hi,

I created tunnel through my ubuntu box:

ssh -f remoteUser@remoteHost -L 2222:remoteHost:22 -N

I see it listening in netstat, I even can connect from ubuntu box:
ssh localhost -p 2222, but when I try to do the same from my pc: 
ssh ubuntuBox -p 2222 I get reject. I don't have any firewall enabled on ubuntu.

What could be a problem to connect to 2222 on ubuntu ?

10x

---

### Post by HermanAB on 2011-03-16
Howdy,

Look at /etc/ssh/sshd_config.  There is a switch in there that can enable/disable remote forwarding.  Read the man page or the Snail Book at snailbook.com since I cannot remember the details.

---

