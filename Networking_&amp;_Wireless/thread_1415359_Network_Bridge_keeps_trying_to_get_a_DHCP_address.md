---
title: "Network Bridge keeps trying to get a DHCP address"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by LingaringBell on 2010-02-24
I have a computer with two network interfaces that I wanted to bridge together. It is running Ubuntu 8.04 Server 32bit. My /etc/network/interfaces config file looks like:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

auto br0
iface br0 inet static
    address 192.168.2.7
    netmask 255.255.255.0
    gateway 192.168.2.1
    bridge_ports eth0 eth1
    bridge_fd 9
    bridge_hello 2
    bridge_maxage 12
    bridge_stp off
    post-up iptables-restore < /etc/iptables.up.rules
```
The bridge seems to work fine, but I see in my syslog that every 5 minutes interface br0 is doing a DHCP Discovery attempt.  Anyone know why it would be doing this?  Thanks.
-Bell

---

### Post by LingaringBell on 2010-02-25
If anyone is curious, I think I figured it out.  I uncommented the section for eth0 and set it to static with no IP.  This fixed the problem.

---

### Post by Iowan on 2010-02-25
Thanks for posting follow-up information. 
[[SOLVED]?]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

