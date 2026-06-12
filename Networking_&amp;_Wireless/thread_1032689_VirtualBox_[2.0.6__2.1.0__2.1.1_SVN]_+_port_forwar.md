---
title: "VirtualBox [2.0.6 / 2.1.0 / 2.1.1 SVN] + port forwarding / host interface networking"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by migajek on 2009-01-06
Hi, 
I installed VirtualBox (tried 3 version, 2.0.6 and 2.1.0 were precompiled packages, 2.1.1 from SVN checked out & compiled yesterday) and I'm running Windows XP as Guest. Host is my Ubuntu 8.10 
Now I'm trying to forward port 9001 on Host to 9000 on Guest. I did as in the manual, but it doesn't work on any of these versions. It seems that the host is listening on the port, but is not forwarding to guest OS (as the server running on guest shows no activity)

I also tried Host Interface Networking on 2.1 and 2.1.1 (selected the only interface I have - eth0) but it was even worse - the guest OS shown no networking at all (I couldn't have browsed the Internet from the guest, while it worked in the default mode)

Is it something about Ubuntu or what? ...

---

