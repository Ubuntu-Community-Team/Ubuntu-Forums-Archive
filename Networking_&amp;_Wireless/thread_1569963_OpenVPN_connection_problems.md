---
title: "OpenVPN connection problems"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by lakerat on 2010-09-07
I have setup an OpenVPN server on Ubuntu server. I am able to connect with Windows clients. I am, however, unable to correctly connect using Ubuntu.

If the router firewall is blocking the pings to keep the connection alive, then the connection initially does not work, but will work after the first timeout and reconnect. If the firewall does not block the pings then the initial connection attempt never times and therefore the connection does not work.

Attached is the readout from the client.

The first attempt gives error ERROR: Linux route add command failed: external program exited with error status: 7

Successive attempts work, they just time out every two minutes. 

Any help would be greatly appreciated.

---

### Post by Hralgmir on 2011-07-08
There is indeed an error message about one third of the way down the listing, Error, Linux route add command failed....etc. Perhaps examining the preceding route add command, using search engines and man.. in the terminal could reveal why this command has failed and what it should do.

---

