---
title: "Odd networking problem"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by urajah on 2009-04-16
I built three Ubuntu 8.10 servers, all in the same /24 subnet. One is a firewall (192.168.10.254), one is a DB server (192.168.10.100) and one is a fileserver (192.168.10.101).

The fileserver cannot ping the firewall by IP, but can ping the DB Server. The firewall and DB Server can ping everyone without problems. AFTER I ping the file server from the firewall, it suddenly becomes able to ping the firewall back.

This means my file server cannot get out to the internet, as the gateway is the firewall (192.168.10.254). If I log into the firewall and ping the file server, it suddenly can ping the firewall and get out to the internet without any problems. This connectivity issue resets after a reboot of the file server. I have a ping job running on the firewall for now to keep the file server happy, but I'd like a real solution and I'm at wits end. The network interfaces all seem fine, the subnets are correct (/24) and matching. I just don't know what else it could be.

Any ideas?

---

