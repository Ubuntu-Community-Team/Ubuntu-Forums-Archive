---
title: "server build"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by carper on 2010-04-16
hi this is what iam aiming for
i have a spare pc with: amd9550 x4
4gig mem
3x 640 gig hds sata
and 2 nics
ive loaded up ubuntu server 9.10 onto this. nic 1 is connected to my isp modem/router
which ive turned off the wap and is hard wired to the server i have a tp link wa5100g wap router that i want to run on nic 2 so my desktops a mix of windows and mint pcs access the net through the server can anyone help me setting this up please the connection to the internet is already available to the server as ive installed webmin and updates

---

### Post by terazen on 2010-04-16
Are you trying to use the server as a router/dns/squid proxy/dhcp server/what?  Can you give more information?

---

### Post by Iowan on 2010-04-16
Capital letters don't cost extra, and punctuation is on sale this week. :)
What doesn't work? NIC 1 (eth0?) can probably be configured for DHCP - I suspect the modem/router will provide it. The [Server Guide]("https://help.ubuntu.com/9.10/serverguide/C/index.html") may provide more answers on Internet Connection Sharing.

---

### Post by carper on 2010-04-16
i want to run all my internet traffic through the server and use the firewall of the router to keep the network safe from internet trafiic to the server as iwant to link the server to a website for file access

---

