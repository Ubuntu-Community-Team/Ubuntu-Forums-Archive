---
title: "Openvpn network access problem"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by mexus on 2010-09-23
I have a tap connection between Ubuntu 10.04 an DD-WRT.
Ubuntu network: 192.168.0.1-192.168.0.229
Server: 192.168.0.1
(lets call it A network)

DD-WRT network: 192.168.0.230-192.168.0.254
Server: 192.168.0.253
(lets call it B network)

My problem is that I can ping A <=> B but I can access rdp, samba, .... only with the host name not IP.
For example
hostname network ip
USER1 A 192.168.0.6
USER2 B 192.168.0.230

USER1 can access (samba, remote desktop connection) USER2 if i type the USER2 (hostname), but If I type the IP of USER2 I get timeout.

It's the same the other way around.

Any Ideas?

Sorry for my english

---

