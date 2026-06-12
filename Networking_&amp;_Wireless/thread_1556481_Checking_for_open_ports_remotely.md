---
title: "Checking for open ports remotely"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by NertSkull on 2010-08-19
So I'm trying to set up an SSH connection from my school to my home, but not on port 22.

I originally tried port 2222, but it didn't work.  I called my school IT people and they said they block that port.  I asked if they care if I set up an SSH and they said no, but that they wouldn't tell me which ports are blocked and which are open for "security" reasons (which I guess I can actually understand).

They suggested just using port 22 or 222, but said if a ports open I can use it.

My question is, can I check ports without setting up SSH?  It seems like a hassle to try a different port every day on my home SSHD file, come to school, see if it works and repeat. 

Is there a way I can check my computer home for connections that could connect, even if there isn't a service listening?  I don't know how to do that, or even if its possible.  

Anyone have any suggestions?  If not, I suspect I'll just try a few until I find something that works, or just go ahead and use 22.  But I always kind of like having things a bit different than standard issue.

Thanks everyone.

---

### Post by sosaited on 2010-08-19
You can check for closed/filtered/open ports with nmap.

---

