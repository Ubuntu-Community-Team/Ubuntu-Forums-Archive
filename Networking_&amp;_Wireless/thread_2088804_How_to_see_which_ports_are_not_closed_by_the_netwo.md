---
title: "How to see which ports are not closed by the network access server?"
date: 2012-11-27
forum: Networking &amp; Wireless
---

### Post by s.v.z on 2012-11-27
Hi! This is not actually an Ubuntu issue, but I'll still be grateful for help. 

I have an Ubuntu PC in a local network with pretty severe policies. All I can do is access the Internet via http or https. No p2p, no ftp, no local network access itself. 

I'd like to know which ports are available for me to communicate with the outer world and if there are any, try to use them. Is there a way to do this?

---

### Post by dannyboy79 on 2012-11-27
you can run nmap -P0 on the external IP address of network you access the internet from. You have to run it from outside that network though. You might be able to use shieldsup though as well to see the open ports.

---

### Post by s.v.z on 2012-11-27
> **dannyboy79 said:**
> you can run nmap -P0 on the external IP address of network you access the internet from. You have to run it from outside that network though. You might be able to use shieldsup though as well to see the open ports.

The ShieldsUp! thing worked, but not the way I expected. It shows that nearly every port is open on my external IP. Looks like there is something in the middle between LAN and the gateway filtering the traffic. Any other options?

UPD: I misinterpreted the results. It's all in stealth mode.

---

