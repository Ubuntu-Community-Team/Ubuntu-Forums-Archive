---
title: "Cannot connect to SSH with UseDNS set to no"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by f00fyf00f3r on 2010-01-30
Cannot connect to SSH with UseDNS set to no

I've been running an 8.04 server via VirtualBox in 9.10. I noticed the connection is slow as heck when I connect and then browse via proxy. I saw someone had said to add "UseDNS no" to sshd_config, so I did such and reloaded ssh. Now, I cannot connect to the server from work today. It was working fine for days prior to the change, I don't get why this would affect my ability to connect. Confirmed the IP address didn't change. I'm trying to get my girlfriend to login to the server and remove the "UseDNS no" but my keyboard is set to Dvorak lol

---

### Post by f00fyf00f3r on 2010-01-30
She was able to remove the line and restart SSH, I am now able to connect in. Anyone else ever have this issue? I don't see anything on it.

---

