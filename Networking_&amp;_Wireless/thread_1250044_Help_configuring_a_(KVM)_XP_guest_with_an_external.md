---
title: "Help configuring a (KVM) XP guest with an external/public static IP"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by yatesco on 2009-08-26
Hi all,

I am running an Ubuntu 9.04 server which has a number of virtual machines.  9 of the virtual machines (it is a beefy box ;)) are Ubuntu 9.04, but now I need to start creating windows machines (xp and 2008 server).

I have been allocated a number of public IP addresses which I have managed to assign to the virtual machines without issue, but I just cannot get it to work in the xp machine.

The host is configured to correctly (at least I can access the Linux virtual machines using their external IP address).

The configuration for the host is:

--- start
# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
      address   78.xxx.xxx.243
      network   78.xxx.xxx.243
      broadcast 78.xxx.xxx.243
      netmask   255.255.255.255
      up route add -host 78.xxx.xxx.1 dev eth0
      up route add -host 78.xxx.xxx.1 dev br0
      up route add default gateway 78.xxx.xxx.1 dev br0
      bridge_ports eth0
      bridge_fd 9
      bridge_hello 2
      bridge_maxage 12
      bridge_stp off
--- end

The configuration for one of the Linux guests:
--- start
auto eth0
iface eth0 inet static
        address 78.xxx.xxx.244
        network 78.xxx.xxx.244
        broadcast 78.xxx.xxx.244
        netmask 255.255.255.255
        up route add -host 78.xxx.xxx.1 dev eth0
        up route add default gateway 78.xxx.xxx.1 dev eth0
--- end

The problem is that when I try and configure the network adapter in windows, it tells me that the netmask cannot be 255.255.255.255.

This is beyond my skills - I don't really understand what the whole "route add -host" thing is, or how to do the window's equivalent.

I have googled and googled my little socks off, but I just cannot find anything relevant (or rather, I don't know enough to know it is relevant).

The XP machine also has another card that is using the KVM DHCP server, and that can browse the net fine, but it is an internal (192.) address.

Please help.

---

### Post by yatesco on 2009-08-26
The answer was provided by the very helpful technical support people at [www.memset.com](www.memset.com) (who are hosting the machine).

The answer is to use a netmask of 255.255.255.0 (windows, as I am sure we all know by now, sucks :)).

---

