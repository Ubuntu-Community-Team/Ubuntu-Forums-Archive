---
title: "Multiple Interfaces 8.10"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by Zeosa on 2009-04-16
I just installed 8.10 server on a new machine with dual built-in NICs and configured it identically to an older testing server (running 8.04). On the new machine however there's a problem. 

I'm trying to bring both interfaces up on the same network, however, whenever eth1 comes up, I lose connectivity through both interfaces. I can either bring up eth0 or eth1, but never both at the same time.

My /etc/network/interfaces:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 10.10.2.180
        netmask 255.255.255.0
        network 10.10.2.0
        broadcast 10.10.2.255
        gateway 10.10.2.1

auto eth1
iface eth1 inet static
        address 10.10.2.190
        netmask 255.255.255.0
        network 10.10.2.0
        broadcast 10.10.2.255
        gateway 10.10.2.1

```

The output of 'route' when both are active
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.6.0     *               255.255.255.0   U     0      0        0 vmnet8
10.10.2.0       *               255.255.255.0   U     0      0        0 eth0
172.16.132.0    *               255.255.255.0   U     0      0        0 vmnet1
default         gateway.shephed 0.0.0.0         UG    100    0        0 eth0
default         gateway.shephed 0.0.0.0         UG    10     0        0 eth1

```

I can delete the second 'default' route (on eth1) and things work again, however I need to bridge this connection to a tun interface for OVPN) so when the bridge comes up, it get yet another default route in the table which again screws things up.

Again, this is set up identically to the 8.04 machine which works as expected.

Any insight?

---

### Post by superprash2003 on 2009-04-16
both are connecting to the same gateway.. i dont know if that causes a conflict.. you could try changing the netmask of one..

---

### Post by Nostalos on 2009-04-16
You don't set up a bridge by configuring both interfaces first.   You configure the bridge interface and set the physical interfaces as manual.

Try this

> 
auto br0
iface br0 inet static
        address 10.10.2.180
        netmask 255.255.255.0
        network 10.10.2.0
        broadcast 10.10.2.255
        gateway 10.10.2.1

    bridge_ports eth0 eth0
    bridge_maxwait 0

auto eth0
iface eth0 inet manual
auto eth1
iface eth1 inet manual



you than add your tun/tap interface to the bridge once you've started the VPN

Adding 2 interfaces both with the same default gateway buys you absolutly nothing.   Configure the bridge interface and be done without having to worry about which interface is up or down or unplugged.

---

### Post by Iowan on 2009-04-16
I've read that having two interfaces in the same subnet confuses routing... I don't have enough experience with bridging and/or TUN interfaces to be of much help.
The *new* Network Manager seems a li'l finicky about static addresses.  There are a few How-To's around (including one by **superprash2003**)

---

### Post by Zeosa on 2009-04-16
> **Nostalos said:**
> You don't set up a bridge by configuring both interfaces first.   You configure the bridge interface and set the physical interfaces as manual.

Try this




you than add your tun/tap interface to the bridge once you've started the VPN

Adding 2 interfaces both with the same default gateway buys you absolutly nothing.   Configure the bridge interface and be done without having to worry about which interface is up or down or unplugged.

I've tried  that as well, I get the same result when br0 comes up and gets it's ip...

---

### Post by Nostalos on 2009-04-17
Then something in hardware isnt right.  Possibly a Bad NIC.  or a NIC that doesnt allow the proper mode for bridging.  Is it a wireless Interface?

As long as both interfaces do not have the same Metric, there is no reason that 2 default routes would break connectivity unless either there was a hardware problem, or they where not connected to the same network.

That configuration I haved used since 8.04 works all the way to 9.04.   Also you can drop the gateway config on eth1.   as long as eth0 is up and working you don't need a gateway on eth1.

---

### Post by Zeosa on 2009-04-18
No wireless on the box, it a Tyan tiger montherboard with 2 NICs onboard.

whats really strange, is I set up a pptp connection on the box while playing around with it, when ppp comes up all other connections drop as well (but the  pppd connection is still alive and well.

For the time being, I've set up a virtual system with vmware on the box hosting another copy of 8.10 and running the vpn through that. It's a workaround, it's ugly, but it works....

---

