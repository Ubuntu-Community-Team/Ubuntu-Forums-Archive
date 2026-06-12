---
title: "Some network/NIC questions"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by Shellbak3 on 2011-04-24
I'm new with Ubuntu.  

My new speciality computer was delivered a week ago with Meerkat installed by the vendor (should be 64 bit but I just realized i forgot to check that!).  It has 2 NICs, one Gigabit and the other 10/100.  The Gigabit port will have a static address and will only be connected to a switch with one or two high tech cameras connected to it.  This port must be dedicated to the application program and the OS or other applications should never attempt to use it even if the 10/100 port is not responding.  The Gigabit NIC is eth1 and the 10/100 is eth0.

I'm not allowed to connect to the work LAN - it won't get an address, it would be detected, and I'd probably be fired so when I need updates etc. I'll take it home.  The 10/100 port will also have a static address on a different network and will be connected to a separate switch with just one other computer on it.

Is it standard for one NIC to be the primary NIC?  How do I tell?
What can I do to dedicate the Gigabit port eth1 to my application?   The SDK/API code that I've implemented "knows" the ip address of the cameras.

Is it possible to upgrade the priority of the Gigabit port?

---

