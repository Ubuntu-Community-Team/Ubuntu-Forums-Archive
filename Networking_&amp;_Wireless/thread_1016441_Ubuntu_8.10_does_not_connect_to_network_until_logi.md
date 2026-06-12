---
title: "Ubuntu 8.10 does not connect to network until login"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by cfmunster on 2008-12-19
After upgrading a couple of machines to 8.10, I noticed that the systems no longer connect to the network at boot time. They now require a user to login before they connect. One of these systems is a server (running Gnome desktop) in the data center and it needs to connect automatically. 

The system has two NICs using a bonded bridged interface with a static IP. 

I understand that I can set up the system for automatic login. I assume that setup will fix the problem. Is there an alternative? I would really rather not have the server auto-login. It's in a secure cage, but still, I'd rather the system connect at boot like it did before I upgraded.

---

### Post by jongkind on 2008-12-20
Network-manager in Ubuntu 8.10 is buggy. I suggest to use wicd instead. It can be installed from here:
[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

When you browse through the forums you'll notice that others also has problems with network manager and that wicd is an adequate alternative.

---

