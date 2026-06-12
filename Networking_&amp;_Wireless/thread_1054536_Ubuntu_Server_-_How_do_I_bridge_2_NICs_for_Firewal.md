---
title: "Ubuntu Server - How do I bridge 2 NICs for Firewall?"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by Gen2ly on 2009-01-29
I'll admit it, I'm a complete dolt when itcomes to networking.  I understand the basics but I need a bit of help with this.

I'm building a server for a home network to use as a firewall.  The pc has 2 NIC's and I going to have the internet come in one, run it through a firewall and output it through the second NIC to my regular computer.

Going through the [documentation]("https://help.ubuntu.com/8.10/serverguide/C/network-configuration.html#bridging") step by step and got to this:

> Bridging

Bridging multiple interfaces is a more advanced configuration, but is very useful in multiple scenarios. One scenario is setting up a bridge with multiple network interfaces, then using a firewall to filter traffic between two network segments

I got lost in the documentation when it only defines one NIC in /etc/network/interfaces:

```
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
        address 192.168.0.10
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
```

So the first question is how do I define the second NIC?  I noticed this [howto]("https://help.ubuntu.com/community/Router") doesn't use bridging.  The second question is are there advantages to using bridging (for ease of configuration, maintenance...) or am I just gnawing my own foot?

---

### Post by Gen2ly on 2009-01-30
Ok, I think I got it.  After a bit of Research it looks like a bridge is used to define two networks cards simaltaneously.  E.g. you have a wired card and a wireless card you'd both like to connect to a LAN network.

---

