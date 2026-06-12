---
title: "Blarg! ssh gets slower and slower, then stops"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by kschaefer on 2009-09-09
I poked around for an answer to this situation, but I must not have the right keyword or somethin'. My ssh sessions are acting up. The ssh daemon is running on Ubuntu Intrepid, and I'm using another Ubuntu Intrepid machine to ssh. When I connect, the connection is nice and peppy for the first few seconds, then it starts to get sticky, then it gets downright sluggish, then it seems to freeze. If I leave it alone for a few minutes, it will come back, and start the process over. I'm running over a local network, NETGEAR wireless router. 

Things I've tried so far:

Adding ClientAliveInterval 20 to /etc/ssh/sshd_config
Adding ServerAliveInterval 5 to /etc/ssh/ssh_config

Any clues would be much appreciated.

---

