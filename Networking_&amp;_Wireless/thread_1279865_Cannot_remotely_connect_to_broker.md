---
title: "Cannot remotely connect to broker"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by jkysam on 2009-10-01
I have an AMQ broker on one machine waiting for incomming connections on port 61616. Localhost connections are not a problem but if I try to connect to it from another machine in the LAN I keep getting a connection refused error. I can ping this machine but not connect against that port.

My iptables is empty:

```
sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```What could be blocking the connection?

---

