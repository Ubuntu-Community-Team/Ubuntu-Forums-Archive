---
title: "help: vpnc requires network-admin magic to get vpn to work"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by d0nv on 2009-09-09
As there have been more than a thousand views on the prior post, I am (belatedly) closing the loop on a [the prior thread under the same title]("http://ubuntuforums.org/showthread.php?t=566761") (which is now archived and unable to be updated).

The issue ended up to be caused by the fact I had two network interfaces (two separate wired ethernet ports) installed/enabled and connected on this machine.  At the suggestion of a local Linux club member, I disabled one of these interfaces and then tried the standard vpnc connect.  It worked fine from there, so I left the second interface disabled permanently to solve my problem.

I had installed the second interface originally to allow access to my local network printer when using Cisco's VPN client in Windows, which restricted local network access.  This was unnecessary in Ubuntu, as I could print fine locally -- even with the vpnc vpn session active on the single interface.

---

### Post by Whiffle on 2009-09-09
I was curious how a thread with no replies could be solved already...


Cool.  Thanks for the followup.

---

