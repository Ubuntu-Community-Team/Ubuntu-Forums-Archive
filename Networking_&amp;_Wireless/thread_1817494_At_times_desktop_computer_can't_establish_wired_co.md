---
title: "At times desktop computer can't establish wired connection"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by avishay on 2011-08-03
Hello all!
My desktop computer, running 11.04 (fresh install) sometimes can't establish a wired Ethernet connection.  Sometimes when I boot, it keeps trying to establish, but with no luck.  I keep trying to choose "Auto eth0" from the networking menu, but still, it doesn't succeed.  If I reboot, it sometimes works.  I can't establish a connection about half the times that I boot.

The computer is connected with a cable to a router ("Belkin Wireless Pre-N router"), and the router is connected with a cable to a cable modem.

I've been using Ubuntu for a while, and I've had a problem for the past few versions (since around 10.04)?  I thought that it might be some old issue that got resolved, so I did a fresh install of 11.04 today, and still have the same behavior.

Any ideas?  I'm willing to try things next time I can't get a connection, but don't know what.

Thanks a lot in advance!

---

### Post by avishay on 2011-08-17
Haven't gotten any responses, but here is some more information.  This computer is dual boot with WinXP, and with Windows I never have a network connection problem.  Also, I used wireshark when Ubuntu was trying to connect and failing, and saw only messages with:

Source: 0.0.0.0
Destination: 255.255.255.255
Protocol: DHCP
Info: DHCP Discover

So there are DHCP requests going out, but no offers coming in.  Any ideas of why this could happen?

---

