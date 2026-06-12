---
title: "Network Not Starting"
date: 2010-12-15
forum: Networking &amp; Wireless
---

### Post by bigtoetag on 2010-12-15
Version 10.04 LTS

Installed desktop version and network worked but I needed a static IP address and the install configures for a DHCP configured address.  I tried changing to static address using the System->Preferences->Network Connections application but was unable to get the system to come up with the network up.  So I manually modified the /etc/network/interfaces and the /etc/resolv.conf files.  I restart the system but when I do an ifconfig, I don't see a configured IP address on eth0 (only the loopback address).  If I run /sbin/ifup eth0 everything then works fine and ifconfig shows the correct address bound to eth0.

My files are as follows:

resolv.conf

nameserver 66.60.130.2
nameserver 66.60.130.6

interfaces

auto lo
iface lo inet loopback
iface eth0 inet static
address 192.168.1.225
netmask 255.255.255.0
gateway 192.168.1.1

Can anybody help with this issue.

Thanks

---

### Post by bigtoetag on 2010-12-17
Got it working.  Added the following to the last line of  /etc/interfaces:

auto eth0

How do I mark this thread as solved?

---

### Post by corncob on 2010-12-17
> **bigtoetag said:**
> Got it working.  Added the following to the last line of  /etc/interfaces:

auto eth0

How do I mark this thread as solved?

Click on "Thread Tools" at the top right of your first post and select "Mark as solved".

---

