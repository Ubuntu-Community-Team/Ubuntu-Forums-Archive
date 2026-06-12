---
title: "how can I force a network interface to be up at startup"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by baronne on 2009-01-07
Hi,
I'm in the process of setting up snort and we're planning on using "stealth" interfaces where they are plugged in, sniffing the network but the interface doesn't actually get an IP address. As a result it seems like the interface is down. If I issue an *ifconfig eth1 up* command, the interface comes up and I can start snort successfully. Unfortunately if the machine is rebooted, that interface goes down again and doesn't come up automagically. 

How can I get the interface to force itself to an "up" state everytime at startup?

cheers
Baronne

---

### Post by baronne on 2009-01-07
I found the solution:

auto eth1
iface eth1 inet manual
 	up ifconfig $IFACE 0.0.0.0 up
        up ip link set $IFACE promisc on
        down ip link set $IFACE promisc off
        down ifconfig $IFACE down


:guitar:

---

