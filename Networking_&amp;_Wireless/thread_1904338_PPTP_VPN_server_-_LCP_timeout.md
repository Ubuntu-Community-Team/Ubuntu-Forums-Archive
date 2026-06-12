---
title: "PPTP VPN server - LCP timeout"
date: 2012-01-04
forum: Networking &amp; Wireless
---

### Post by AwilZini on 2012-01-04
I would like to have a PPTP VPN server on my ubuntu server.
 
 I installed and configured pptpd but it doesn't work.
 Any connection to the VPN from outside is impossible, from the LAN it works  but I don't know if it has any meaning. By the way the PPTP is authorized  on the router.
 
 Here's what says the server's log:
```

pppd[31606]: Using interface ppp0
pppd[31606]: Connect: ppp0 <--> /dev/pts/1
pppd[31606]: LCP: timeout sending Config-Requests
pppd[31606]: Connection terminated.
pppd[31606]: Modem hangup
```As you can see, I always get this LCP timout.

The strange thing is that the first time I configured all of this, I was  able to connect to the VPN. But then by trying to get the access to  Samba on LAN I lose the access at all. Now even after an "apt-get --purge  remove pptpd" I cannot get it work.

Any idea ?
If you need more information just ask me.

---

