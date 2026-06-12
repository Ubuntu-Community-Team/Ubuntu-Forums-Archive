---
title: "network card missing from virtual machine"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by midlifecrisis on 2009-12-14
Please help,

I'm running ubuntu 8.04LTS via Parallels on my macbook. I've just fired up ubuntu and there is no network card.

from ifconfig -a it only shows the 'lo'

I've had a search and worked through some of the 'udev' solutions, but they haven't helped.

/etc/network/interfaces shows 'lo' and 'eth0'

I don't have an /etc/iftab

To make matters worse, there is also a problem with parallels tools and I have no mouse pointer.

Any advice would be great, but please assume I know nothing.

Cheers

---

### Post by shairozan on 2009-12-14
Hey there, 

If it's anything like VMware or Virtualbox, they won't show anything until the device is "connected". For the configs on the virtual machine, is there an option that says something like "connect at startup" for the NIC?

---

### Post by midlifecrisis on 2009-12-14
I can't see a 'connect at startup' option, but I have changed parallels network settings between bridged to shared and enabled DHCP. I can see the network interfaces in the mac network preferences for parallels. I've also plugged in a network cable to see if the physical cable would connect, but no success yet.

---

