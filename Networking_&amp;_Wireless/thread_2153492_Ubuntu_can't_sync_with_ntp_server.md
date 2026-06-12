---
title: "Ubuntu can't sync with ntp server"
date: 2013-06-11
forum: Networking &amp; Wireless
---

### Post by jorestiq on 2013-06-11
Hi every one,

I messed up with ubuntu server 12.10 3 mounts ago so i am new. My problem is: I have got a server with 3 NICs two of them in private networks and one my local LAN. The default gw is looking to one of the private networks which do not have route to public internet. Its essential the server time to be precise. So when i try to sync with a ntp server
 Can't find host 0.bg.pool.ntp.org: Name or service not known (-2). I thing that it should be set a static route to local gw which cat route the traffic out. But ntp server change it ip every time. If some one can help it would be great.

Best regards

---

### Post by SeijiSensei on 2013-06-11
Am I correct in thinking this machine has no interface with a direct route to the Internet? If you need to configure specific IP addresses for NTP, just run a "host 0.pool.ntp.org" to get addresses for some of the pooled servers and use those.

If this machine cannot see the Internet at all, then you'll need to enable an NTP server on some other Internet-facing machine that you can connect to and use that as your NTP server.

---

