---
title: "IPv4"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by Ilda on 2009-11-05
Hi,
I just recently installed a new NIC and eth1 is not acquiring the IPv4 address as you can see below.

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:18:f1:8e:72
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fef1:8e72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:478 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:116666 (116.6 KB)  TX bytes:20883 (20.8 KB)
          Interrupt:26 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:a1:b0:69:34:b6
          inet6 addr: fe80::2a1:b0ff:fe69:34b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:25836 (25.8 KB)  TX bytes:468 (468.0 B)
          Interrupt:22 Base address:0x8c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

What do you suggest to solve this?
I am very new to Ubuntu.
Thanks

---

### Post by Brandon Williams on 2009-11-05
Please let us know how you are expecting this to work. Are you counting on network-manager to automatically get an address for you? Or did you configure the new interface in /etc/network/interfaces?

---

### Post by regala on 2009-11-05
> **Ilda said:**
> Hi,
I just recently installed a new NIC and eth1 is not acquiring the IPv4 address as you can see below.

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:18:f1:8e:72
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fef1:8e72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:478 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:116666 (116.6 KB)  TX bytes:20883 (20.8 KB)
          Interrupt:26 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:a1:b0:69:34:b6
          inet6 addr: fe80::2a1:b0ff:fe69:34b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:25836 (25.8 KB)  TX bytes:468 (468.0 B)
          Interrupt:22 Base address:0x8c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

What do you suggest to solve this?
I am very new to Ubuntu.
Thanks

see, many things can cause this, did you at least put something into /etc/network/interfaces related to eth1 ? it can't guess what you want it to do, and it won't try to do what eth0 is configured to do.

Did you put a cable on a network with a dhcp server running ? did you configure /etc/network/interfaces ?

please provide the /etc/network/interfaces file please.

br

---

### Post by Iowan on 2009-11-05
Did you intend to use both interfaces, or will you disable one (or the other)?

---

### Post by Ilda on 2009-11-11
I am sorry for being so late

I did something wrong and everything stopped working.
Fortunatelly it's working now.
I am trying to use both network cards at same time
eth0 is a onboard one
eth1 is a PCI one. I'd tested it on windows and works perfectly.

I am not sure if it has some relation, but after using the following commandfs eth1 started working.

sudo lshw -C network
sudo dhclient eth 1

does it has some relation?

I don't know where network-manager is. I am using the server version.
I didn't touched  /etc/network/interfaces
Yes, both are connected to a router with dhcp enabled

Very thanks all of you

---

### Post by Ilda on 2009-11-11
the /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


Now everytime I turn on the computer I have to use
sudo lshw -C network
sudo dhclient eth1

How can I do this "programatically"?

Very thanks

---

### Post by falconindy on 2009-11-11
> **Ilda said:**
> the /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


Now everytime I turn on the computer I have to use
sudo lshw -C network
sudo dhclient eth1

How can I do this "programatically"?

Very thanks
Make a new section below the last

```
auto eth1
iface eth1 inet dhcp
```

btw, lshw (list hardware) doesn't have anything to do with enabling a NIC. dhclient was doing the work as a DHCP client; scanning for a server to get an IP from.

---

