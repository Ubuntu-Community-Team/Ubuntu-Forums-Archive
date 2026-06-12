---
title: "Ad Hoc Not working"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by Rishav Thakker on 2011-01-22
Hey everyone.

I use an Ubuntu 10.10 Maverick Desktop 64 bit, on a HP Pavilion dv2601tx.

So what I want to do is create an Ad Hoc connection so that I can share my internet connection to my iPod touch

I'm successfully able to create an AdHoc connection via the network manager applet (ie Ubuntu shows "connected to <network name>"). My connection settings are:

Name: UbuntuAdhoc
encryption: WEP (I've tried unsecure too)
IP: Shared to others.

But the problem is that no other device (My iPod or any other computer) can connect to this network. My iPod just tries to connect, and after a few minutes says "Could not connect to UbuntuAdhoc"

Sometimes, when I connect my computer to some other network (for eg a network from a router), and then disconnect and create this AdHoc, it works (ie the iPod connects).

Wireless hardware information (lspci output):

-----------------------------------------------------------------
Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
        Subsystem: Hewlett-Packard Company Device 135b
        Flags: bus master, fast devsel, latency 0, IRQ 47
        Memory at f4100000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: iwl3945
        Kernel modules: iwl3945
-----------------------------------------------------------------

NOTE: It used to work fine in Lucid.

I've searched extensively online and couldn't find a solution.
If someone could help it would be really appreciated.

Thanks. :)

---

