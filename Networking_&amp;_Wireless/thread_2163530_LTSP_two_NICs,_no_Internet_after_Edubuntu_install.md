---
title: "LTSP: two NICs, no Internet after Edubuntu install"
date: 2013-07-18
forum: Networking &amp; Wireless
---

### Post by stupidscript on 2013-07-18
HP Proliant w/4-NICs ... using 2 for this

- Installed Edubuntu 12.04 LTS with the LTSP server.
- Chose eth1 for serving DHCP to LTSP clients.
- eth0 is connected to existing network.
- Existing network has router that also does DHCP.
- During installation, eth0 Internet connection worked fine, got updates and whatnot.
- After installation ... no Internet from either NIC.

ifconfig basically shows:

eth0 got IP from router's DHCP (192.168.0.137)
eth1 is static assigned at the top end of the router's assignment block (192.168.0.254)

No IP collisions with other systems attached to the router.

(There's also an LXC bridge interface (lxcbr0), if that makes any difference.
I can kill LXC without helping this issue and seemingly without affecting LTSP logins.)

When eth0 is attached to the rest of the network (and the router), I can't ping anything.
When eth0 is attached, I can see 'Windows Network' but can't connect to it.

When eth1 is attached to the rest of the network, I can ping other computers on the network, but no Internet.
When eth1 is attached, I can see all Windows shares on the network using smbtree but not with the Networking app, which shows the Workgroups, but cannot access them.

Weirdly, from other machines on the network, with eth1 attached to the network and eth0 attached to nothing, I can ping both the eth0 address (.137) and the eth1 address (.254).

In no case can I access the Internet with either the Edubuntu server or (obviously) the LTSP clients.

Ideally, I would leave eth0 attached to the network and router and leave eth1 attached to the switch that the LTSP clients are attached to. That, after all, is the only way the LTSP clients will boot in this setup.

I do realize that pretty much every installation guide says that there might be DHCP issues hooking up the LTSP box to a network with another DHCP assigner (the router) in it, however I'm guessing this is a routing issue within the Edubuntu box, and not related to whether the router is assigning IP addresses or not.

Been wrong, before. ;)

Here's a little something that makes me lean toward a routing problem: the output of 'route' on the Edubuntu box:
```

Kernel IP Routing Table
Destination   Gateway   Genmask   Flags   Metric   Ref   Use Iface
default   192.168.0.1   0.0.0.0   UG   100   0   0 eth0
10.0.3.0      *   255.255.255.0   U   0   0   0 lxcbr0
link-local    *   255.255.0.0   U   0   1000  0 eth1
192.168.0.0   *   255.255.255.0   U   0   0   0 eth1
192.168.0.0   *   255.255.255.0   U   0   0   0 eth0

```
The last two entries look suspiciously like the routing table would have a hard time figuring out which interface to use.

I still haven't figured out what the bridge is for (lxcbr0). Maybe that's where I need to look?

I am happy to post config or probe info, as needed. Thanks in advance for any guidance.

---

### Post by newbie-user on 2013-07-18
A few issues:
1) Both interfaces are on the same network, 192.168.0.0/24, and that will definitely cause all sorts of problems, especially since your LTSP server is doing DHCP.
2) As you mentioned, having two routes might be causing problems due to #1 above.
3) If you actually do intend on having your thin clients on the same network, you need to have only a single DHCP server that passes out the proper boot configurations to the thin clients.
4) If #3 above is your actual intention, then you need only to use a single NIC for LTSP, unless you want to load balance between the two NICs

Having your LTSP server separate from your DHCP server isn't an issue at all. Assuming your DHCP server is Ubuntu, then your DHCP configuration would include the following lines:
```
next-server *[ip address of ltsp]*;
filename "/ltsp/i386/pxelinux.0";
option root-path "/opt/ltsp/i386";
```

---

### Post by newbie-user on 2013-07-18
Wait, maybe I misread something in your post... Is you setup like this?

Router ------(eth0) LTSP server (eth1)------switch------thin clients

If so, then just put eth1 on a different subnet and change your LTSP DHCP accordingly.

---

### Post by stupidscript on 2013-07-19
Thanks for your reply!

You're right in the second post ... that's how it's currently set up. And that's where I'm heading, today ... different subnet for LTSP.

I figure:

Router (192.168.0.1) => eth0 LTSP eth1 <= (192.168.1.1) <= thin clients

Do you know what the (lxcbr0) bridge is for? Should I be using 10.0.3.1 for something?

The Ubuntu 12.04 LTS version of auto-installed LTSP does not create one. Just the Edubuntu version does.

---

### Post by newbie-user on 2013-07-19
I don't know what that bridge is for. I've never done LTSP using Edubuntu, only did it with regular Ubuntu.

Haven't done LTSP in a while, so I don't remember if you need to enable ip forwarding. I think you do, so in /etc/sysctl.conf uncomment the line
```

#net.ipv4.ip_forward=1

```

---

