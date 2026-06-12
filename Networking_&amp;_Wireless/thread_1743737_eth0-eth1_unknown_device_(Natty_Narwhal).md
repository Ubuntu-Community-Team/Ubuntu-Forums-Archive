---
title: "eth0-eth1 unknown device (Natty Narwhal)"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by johnbrown105 on 2011-04-29
Hello All,

I have two network cards. In Maverick Meerkat(?), they looked like this:

eth0 - static private IP address, connected to local network (on-board NIC)
eth1 - DHCP public address, connected to cable modem (PCI NIC).

The Internet connection is shared with the private network using Firestarter.

After upgrading to Natty Narwhal yesterday, I now have:

eth1 (no IPv4 address.)
eth0-eth1 (DHCP address from cable modem).

What is an eth0-eth1?

When I click on the Indicator applet (up and down arrows), it tells me that my on-board NIC is disconnected, but this is not true, as I have a link light at the computer and naturally a corresponding light at the hub.

I can get on the Internet (thank goodness, or I would not be able to post this!) but I cannot connect to the local network. Please help me to get back to my original configuration.

---

### Post by johnbrown105 on 2011-05-01
It seems to have solved itself. I still wish I knew how to fix it, but the important thing is that everything is working.

---

### Post by johnbrown105 on 2011-05-11
The problem has re-appeared. Can someone tell me which file to edit? /etc/network/interfaces has eth0 and eth1 but the output of ifconfig shows eth1 and eth0-eth1.

---

