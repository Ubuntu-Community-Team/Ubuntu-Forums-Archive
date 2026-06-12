---
title: "How to log VPN connection details"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by olki on 2010-09-01
Hello,

I've set up a VPN server (poptop) but upon successful connection, I can't see in the syslog which user logged in. I got something like:

pppd[28069]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Aug 31 15:49:51 firewall pppd[28069]: pppd 2.4.5 started by root, uid 0
Aug 31 15:49:51 firewall pppd[28069]: Using interface ppp0
Aug 31 15:49:51 firewall pppd[28069]: Connect: ppp0 <--> /dev/pts/0
Aug 31 15:49:54 firewall pppd[28069]: MPPE 128-bit stateless compression enabled
Aug 31 15:49:56 firewall pppd[28069]: local  IP address 172.19.1.6
Aug 31 15:49:56 firewall pppd[28069]: remote IP address 172.19.1.31
Aug 31 15:51:31 firewall pppd[28069]: LCP terminated by peer (o^Z^W^Z^@<M-Mt^@^@^@^@)
Aug 31 15:51:31 firewall pppd[28069]: Connect time 1.6 minutes.
Aug 31 15:51:31 firewall pppd[28069]: Sent 107198 bytes, received 368179 bytes.
Aug 31 15:51:33 firewall pppd[28069]: Modem hangup
Aug 31 15:51:33 firewall pppd[28069]: Connection terminated.
Aug 31 15:51:33 firewall pppd[28069]: Exit.

Is there a way to log the user name as well?

Thank you very much.

---

