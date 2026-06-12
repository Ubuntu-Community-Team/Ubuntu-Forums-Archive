---
title: "Two Network Cards on two networks"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by IbuildDW on 2009-05-28
I hope this is a simple problem, thanks in advance for the help.

I have a system with two NICs 

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.123.22
        netmask 255.255.255.0
        network 192.168.123.0
        broadcast 192.168.123.255

# Seconday network interface
auto eth1
iface eth1 inet static
        address 10.1.1.22
        netmask 255.255.255.0
        network 10.1.1.0
        broadcast 10.1.1.255
        gateway 10.1.1.21

Each is going to listen for different things.  The problem I'm having is:

Before I added the eth1 I was able to ssh into the eth0 address and after adding and bringing it up I'm unable to.  I searched for help and thought I fixed it when I removed the gateway from eth0 (there were two) and now route looks correct.

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.123.0    *               255.255.255.0   U     0      0        0 eth0
10.1.1.0        *               255.255.255.0   U     0      0        0 eth1
default         10.1.1.21       0.0.0.0         UG    100    0        0 eth1

what else am I missing?  I'd like to be able to ssh to this server from both networks, is this possible?

---

### Post by Iowan on 2009-05-29
Can you SSH into it from eth1 network?

---

### Post by IbuildDW on 2009-06-01
> **Iowan said:**
> Can you SSH into it from eth1 network?

With some more investigation, it appears I didn't describe the issue properly.

I can SSH into it from either network.  My testing was from a third network (vpn)  the problem appears to be with the gateway for eth1.  Though I have ip forwarding configured on the 10.1.1.21 machine, it isn't working.  At least that's what I currently think the problem is.

---

