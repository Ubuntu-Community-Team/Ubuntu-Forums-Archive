---
title: "Can't get lan working through eth2"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by gene02 on 2009-02-04
My machine (gutsy 7.10, kernel 2.6.22-16) has three ethernet interfaces.  eth0
which is built into the motherboard faces the internet, eth1, a Realtek gigabit
ethernet card, faced my home lan, and eth2 went unused.  I posted a separate
issue today regarding being unable to bring eth1 up after a reboot yesterday.  As a
workaround, I tried getting eth2 going instead.  I can bring eth2 up, but I am not
getting a working lan.  Any advice would be greatly appreciated!

The contents of /etc/network/interfaces are:
```

auto lo
iface lo inet loopback

iface eth0 inet static
address <xxx.xxx.xxx.xxx>
netmask 255.255.255.0
gateway <xxx.xxx.xxx.xxx>
auto eth0

iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

iface eth2 inet static
address 192.168.0.1
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255

```
(note, I redacted my ip address in the eth0 block)

Here is the output of route -n:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
<xxx.xxx.xx.0>  0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
0.0.0.0        <xxx.xxx.xx.1>    0.0.0.0         UG    100    0        0 eth0

```
(my ip address and gateway are redacted again, guess I'm paranoid)

And here is the output of ifconfig (again with redactions):
```

eth0      Link encap:Ethernet  HWaddr <XX:XX:XX:XX:XX:XX>
         inet addr:<xxx.xxx.xx.xx>  Bcast:<xxx.xxx.xx.255>  Mask:255.255.255.0
         inet6 addr: <xxxxxxxxxxxxxxxxxxx> Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:202326 errors:0 dropped:0 overruns:0 frame:0
         TX packets:123312 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:24217884 (23.0 MB)  TX bytes:52531294 (50.0 MB)
         Interrupt:7

eth2      Link encap:Ethernet  HWaddr 00:0A:CD:13:6B:9E
         inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:282 errors:0 dropped:0 overruns:0 frame:0
         TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:26931 (26.2 KB)  TX bytes:756 (756.0 b)
         Interrupt:11

lo        Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:59212 errors:0 dropped:0 overruns:0 frame:0
         TX packets:59212 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:16312967 (15.5 MB)  TX bytes:16312967 (15.5 MB)

```

To me, that looks like a working configuration.  The link lights on the ethernet
card and on the hub it attaches to are on, but I just can't get any internet from
any computer attached to the hub.

If there is any other info you need to help me figure this out, please let me
know.

---

### Post by gene02 on 2009-02-05
I did make some progress on this, so now it is half working.  First, I discovered that the shorewall firewall configuration was interfering with my setup.  Specifically, eth1 was defined in the shorewall files, but not eth2.  So I replaced all references to eth1 by eth2 and restarted shorewall.  Running tcpdump, I could finally see incoming pings from a test machine on my home lan, but no return pings going back out.  Having gotten the eth1 card working again, I switched the configuration back to eth1 and that worked normally -- accepting and returning pings.  Switching to eth2 again, I again saw only incoming pings with nothing going out.

Any suggestions on getting it to work?

---

