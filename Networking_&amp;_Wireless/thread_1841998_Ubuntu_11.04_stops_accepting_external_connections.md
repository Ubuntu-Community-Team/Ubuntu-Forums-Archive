---
title: "Ubuntu 11.04 stops accepting external connections"
date: 2011-09-10
forum: Networking &amp; Wireless
---

### Post by rhsanborn on 2011-09-10
I've setup both an Ubuntu Server 11.04 64-bit, as well as an Ubuntu Desktop 11.04 64-bit (on the same computer). The only available network connection is via a Belkin USB Wireless adapter. With the desktop it was setup with NetworkManager. With the server, it's setup to start using rc.local.

I installed OpenSSH server. When I first start the box I can ping it from other machines on the internal network, and I can connect via SSH. Randomly, SSH pukes on the client and claims the host is down, and I can't reconnect, and I can't ping it. If I go to the console I can still ping outbound. If I reboot the server, I restart the cycle all over again.

Any ideas?

Regards,

Randall

---

### Post by rhsanborn on 2011-09-11
Replaced a Belkin router with a new Netgear N600 today, and everything has been running swimmingly. Looks like router problems.

---

### Post by lkjoel on 2011-09-11
Could you mark this thread as solved? Thread Tools->Mark this thread as Solved.

---

