---
title: "Network teaming over multiple servers?"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by toxicdav3 on 2009-05-24
I got a bunch of servers connected to an internal network via eth1 and eth0 is to the internet. Just wondering if its possible to team eth0 over all the servers so my internal network becomes public and has 4x the speed to the internet?

---

### Post by JeppeM on 2009-05-25
You could make a round-robin system on the gateway the clients use, so that they'll be using different gateways. But i dont think it's possible to get "4x the speed"... How many clients do you have one the internal network? And are the servers connected to different ISPs, or are they all connected to the same line out to the internet?

---

### Post by toxicdav3 on 2009-05-25
This whole internal network is virtual for hosting Xen servers. I was thinking just setup a vpn for eth0 on each server and bond the virtual adapters. Possible?

---

