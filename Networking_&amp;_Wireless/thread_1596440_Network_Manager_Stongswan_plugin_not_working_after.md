---
title: "Network Manager Stongswan plugin not working after upgrade 10.04 - 10.10"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by Bow rat on 2010-10-14
Hi all,

Thanks in advance for any assistance that anyone can provide.

I upgraded from 10.04 to 10.10. Amongst the things that broke was the network manager strongswan plugin that provides IPSec VPN.

It connects to my VPN server, but does not do NAT-T (moving the session to udp/4500), instead sticking with udp/500 which doesn't work and the connect session times out.

Has anyone experienced similar symptoms and have they found a solution?

Cheers!

---

### Post by Bow rat on 2010-10-16
Huge kudos & accolades to Alfalfa for finding a thread in German that states that there is a bug in the /etc/strongswan.conf file not loading the correct modules.

See Alfalfa's post here: [http://ubuntuforums.org/showthread.php?t=1597421](http://ubuntuforums.org/showthread.php?t=1597421)

Thanks Alfalfa & original poster from University of Freiburg!

---

