---
title: "force eth1 &amp; eth0 on specific hardware?"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by wkearney99 on 2010-03-04
I've got a machine running 9.10 with two network interfaces, one being motherboard based (atl1) and the other in a PCI slot (e100).  By default at boot the interfaces come up in the wrong order.  I'd prefer to have the e100 come up as eth0 instead of eth1.  And then have the atl1 come up on eth1 instead of eth0.    Both interfaces use static addresses and IP4 routing should be active across them.  Where do I configure things to force the specific settings?

---

### Post by r939ick on 2010-03-05
I don't have a dual-homed 9.10 machine handy to test this out on, but in general, the trick is to force the drivers to load in the order you want the interfaces to be enumerated.  So, in /etc/modules, list "e100" before "atl1", each on a line by themselves.  Swap the config for eth0 and eth1 in /etc/network/interfaces, and reboot.

If you want the machine to act as a router for other devices on the two networks, uncomment the line in /etc/sysctl.conf that reads:

#net.ipv4.conf.default.forwarding=1

---

### Post by suseendran.rengabashyam on 2010-03-05
Hi,

Open the file /etc/udev/rules.d/70-persistent-net.rules and make the following changes:

Replace NAME="eth0" with NAME="eth1"

and

Replace NAME="eth1" with NAME="eth0"

Reboot the computer for the changes to take effect.

Verify your changes using the command
sudo lshw -class network

Hope it helps.

---

