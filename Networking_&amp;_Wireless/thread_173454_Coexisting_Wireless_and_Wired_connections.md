---
title: "Coexisting Wireless and Wired connections?"
date: 2006-05-10
forum: Networking &amp; Wireless
---

### Post by EReckase on 2006-05-10
I have a HP Pavilion dv8000 running 32-bit Breezy.  This laptop has one of the Broadcom 4318 wireless chipsets inside it - using ndiswrapper, I'm able to get the driver loaded and I'm able to use the wireless connection.  My problem is on boot-up, though.

When the machine first starts, both the wired and wireless interfaces are both 'active' on the network settings dialog.  If I try to connect to the internet, I get no connection.  Here's what route -n looks like:

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         10.0.0.2        0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         10.0.0.2        0.0.0.0         UG    0      0        0 eth0

```

I can ping the router but I can't ping any outside IP.

Once I manually disable the wireless in the network settings, I'm able to connect to the outside world without issue.  My /etc/modules has ndiswrapper included at the end, I performed a ndiswrapper -m, and this is my /etc/network/interfaces file:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface

iface wlan0 inet dhcp
wireless-essid XXXXXX
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXX

iface eth0 inet dhcp

auto eth0
```

How do people have both wireless enabled and wired connection take priority?  Am I just configured incorrectly?

Thanks!

---

### Post by mips on 2006-05-10
```

10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 wlan0
```

NO. This will not work. You can not have two interfaces on the same machine within the same network. You can have 10.0.0.0 & 10.0.1.0, this offcourse means your router must be able to have it's wireless & wired interfaces configured accordingly.

You could try nic bonding but I don't know how well that will work with wired & wireless.

[http://www.ubuntuforums.org/showthread.php?t=129159](http://www.ubuntuforums.org/showthread.php?t=129159)
[http://www.ubuntuforums.org/showthread.php?t=99668](http://www.ubuntuforums.org/showthread.php?t=99668)
[http://www.ubuntuforums.org/showthread.php?t=163453](http://www.ubuntuforums.org/showthread.php?t=163453)

**_WHY?:_**
[http://www.unet.univie.ac.at/aix/aix...interfaces.htm](http://www.unet.univie.ac.at/aix/aix...interfaces.htm)
> **Implications of Multiple Network Interfaces on the Same Network**

Sometimes network managers feel the need to provide greater availability and performance by adding a second network adapter to a particular machine. For example, they may want to have two token-ring adapters attached to the same physical network. While it is possible to have more than one interface on the same network, in general this is not recommended for two reasons:

1. Having two interfaces on the same network is a violation of TCP/IP architecture.

In TCP/IP architecture, a host machine with two network adapters is defined as an IP router. Different network adapters must be attached to different physical networks. In the case of token-ring, TCP/IP addresses multiple rings bridged together as a single logical ring (as if it were a single physical ring).
2. Having two interfaces on the same network can cause broadcast storms.

Whenever an IP host sees traffic for a network whose IP address is different from its own network, it generates an Internet Control Message Protocol (ICMP) packet announcing this conflict. Since every host on the network sees the traffic that is misaddressed, every host generates ICMP packets. If the amount of misaddressed traffic is significant, the ICMP traffic can grow to the point that network performance degrades.

It is possible to avoid the broadcast storms created when multiple interfaces are connected to the same network. However, doing so is still a violation of TCP/IP architecture. The solution is to give the different interfaces different IP addresses on the same network. For example, you might have two token-ring adapters on the same network named tr0 and tr1. You must assign distinct IP addresses and names to tr0 and tr1. (TCP/IP architecture requires that each interface have a unique IP address and name; otherwise, unpredictable behavior will result.) For instance, you might give interface tr0 the IP address 10.10.10.1 and the name laurel.foo.bar.com, and interface tr1 the IP address 10.10.10.2 and the name hardy.foo.bar.com.

---

### Post by EReckase on 2006-05-10
I believe I've been bitten by the wifi-radar incompatibility with Broadcom chipsets.  Once I uninstalled wifi-radar, everything works properly.  Is there any sort of wireless connection manager that is recommended since wifi-radar doesn't work correctly?

---

