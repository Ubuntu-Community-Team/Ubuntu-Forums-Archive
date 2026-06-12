---
title: "DHClient fails to autodetect correct IP from ISP"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by dualbootguy on 2009-03-12
My internet (rogers cable) works in sh*tty old windows XP, finding the new ip address leased to me. Its not a fixed IP. 
Ubuntu 8.10 keeps trying to implement a previously used IP. I've tried the basics... restarting the machine with no connection, restarting the modenm and then making the connection, restarting the network interface completely, using dhclient to force IP lease renewal of eth0. Everything just brings back the old ip... which has a connection and I can ping sites like yahoo.com, but, because it is not the IP actually assigned by the server, I have no ability to browse or for that matter do anything beyond pinging an address. Setting as a static IP at the correct address doesn't work either. The rogers servers don't accept static IPs (unless you make a deal and pay extra for them). The issue came up shortly after my last regular upgrade, though since reverting to an earlier version doesn't solve the problem, I can only guess that it may be a problem with a configuration file some where. Not sure.

If anyone has any ideas, I'd love to hear them. I'm at a loss, forced to use windows for the time being (which i hate) and missing my 'buntu.

---

### Post by dualbootguy on 2009-03-14
Found the problem. Firestarter.  ...after all the hassle, and after trying to reconfigure it once I knew it was the problem, I've removed it. POS kept misinterpreting the ip being assigned and was somehow messing with the config settings even after being shut down. Someone should look into this as its way out of my league.

---

