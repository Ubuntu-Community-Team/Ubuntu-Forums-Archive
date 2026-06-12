---
title: "Wired network become unresponsive"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by ThomWilhelm on 2009-08-24
Hello there, I am running Ubuntu desktop 9.04 for running a MySQL server. My problem is that every few days the wired network of this computer becomes unreachable from other computers on the local network. There is no wireless network activated on the server.

I started by using NetworkManager, but tried to solve the problem by just writing a /etc/network/interfaces file with the following config:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 169.254.200.190
netmask 255.255.255.255
gateway 169.254.200.190

Every few days without warning the server cannot be accessed from the webserver which is at IP 169.254.202.245, I can solve the problem by running /etc/init.d/networking restart.

However I would prefer to solve the problem without running that command manually every few hours, and running it from a cron still doesn't really deal with the cause.

Any advice would be great.

Thanks,
Thom.

---

### Post by Iowan on 2009-08-24
Have you checked **ifconfig -a** when machine becomes unresponsive - in case it's changing addresses.

---

### Post by dbalascak on 2009-08-24
The host IP equals the gateway and it is using a full mask.  Never seen anything quite like that.  What is the mask of other systems that use a similar IP address 169.254.20x.y?

---

### Post by ThomWilhelm on 2009-08-26
Right Ok, I've done some research and have now changed the mask from 255.255.255.255 to 255.255.0.0 (this is the same for all other devices on the network), allowing computers on the network with IP addresses 169.254.x.x to be seen as local devices.

This was the only computer on the network with this full mask, but strangely enough the same unresponsive problem happened this morning with the new partial mask! I had not read this thread before then otherwise I would have used the ifconfig -a command and that might have solved it, still /etc/init.d/networking restart has done the trick for now.

Thanks very much for your help so far! I'll post back next time the problem happens and I've run that command...

---

### Post by ThomWilhelm on 2009-08-27
Ok its happened again just now. I ran ifconfig -a and everything is fine in terms of configuration. I notice for eth0 it says that 

TX packets:9692290 errors:154 dropped:0 overruns:154

Could this be something to do with the eth0 crash? Is there a log file for this?

---

