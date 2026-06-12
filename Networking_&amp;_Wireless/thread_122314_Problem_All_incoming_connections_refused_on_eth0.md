---
title: "Problem: All incoming connections refused on eth0"
date: 2006-01-27
forum: Networking &amp; Wireless
---

### Post by chrestomanci on 2006-01-27
I have a system running Kubuntu on and AMD64 system.

Recently it has started refusing all incoming network connections. I am running various network services (Squid, Apatche, etc), but when I try to connect from another computer on my LAN, I get a connection refused error. There is never any mention of a connection attempt in the log files of these services.

Connections from the same system via loopback work OK, outgoing connections to the public internet also work fine.

I think that some sort of firewall is blocking the connection attempts. I have tried using firestarter to reconfigure the firewall but it does not work. The firestarter logs show lots of UDP packets from the internet, but no TCP connections.

I think that a second firewall has been installed as part of the Kubuntu install. How do I reconfigure so that I can run my services?

Thanks.

---

