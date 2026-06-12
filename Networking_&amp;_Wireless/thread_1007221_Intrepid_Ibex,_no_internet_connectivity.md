---
title: "Intrepid Ibex, no internet connectivity"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by mattmole on 2008-12-10
Hi all,

I have an RM nBook 100 laptop (I believe it is a rebadged Fujitsu-Siemens) with 1Gb/s wired network connection, and a wireless card.

Ubuntu Intrepid does not support the wireless card, so the problem sits with the wired internet adapter.

When booting and logging in the machine selects an IP in the correct range, the subnet mask is as expected, as are the DNS servers, and the gateway address.

I then cannot access any websites either using a tool such as wget or firefox.

I can carry out an nslookup, and the results returned are correct, I cannot however access this website, even via the IP.

I can ping machines internal to the network (but not external, this is a property of out network connection).

Everything else seems to work, I can access samba/windows shares etc

I am at a loss, I have tried this with numerous Intrepid installs, I have also tried Hardy and openSUSE. The kernel modules loaded are the same as on a working machine, as are the iptables rules.

To add interest to the problem, the internet connection works perfectly well using a live disk! I have also compared settings with the livedisk and I cannot see anything wrong.

I have tried three separate IP addresses on our network and I return nothing!

Traceroute seems to suggest my connection "breaks" at the gateway level.

Finally, Windows XP (installed on the machine) does not see this problem!

I have Kernel version 2.6.27-7, and I have tried installing 2.6.27-9

Cheers in advance!

---

### Post by iponeverything on 2008-12-10
funky -- maybe it's a mtu issue - and something has DF set.

---

### Post by mattmole on 2008-12-10
I have changed the MTU size to a large number (using network manager) (300bytes) and the connectivity has returned. How do I change this setting permanently?

---

### Post by superprash2003 on 2008-12-10
this should help [http://prash-babu.blogspot.com/2008/06/how-to-change-mtu-values-in-linux.html](http://prash-babu.blogspot.com/2008/06/how-to-change-mtu-values-in-linux.html)

---

### Post by iponeverything on 2008-12-10
it should stick when you set it under NM.

---

