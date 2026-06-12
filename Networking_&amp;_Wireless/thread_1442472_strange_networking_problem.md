---
title: "strange networking problem"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by nhk on 2010-03-30
Hi ubuntuforums!

I am running a server that needs both a wired and wireless connection with static IPs, with wireless as the default link.  I'm using the SMCWUSB-G for wireless.

I was running Debian for a while and had some routing tables set up as in [http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html) .  Everything worked until I recently switched to Ubuntu Server 9.10.  After the switch a weird behavior showed up: if wlan0 is down, eth0 works fine.  But if wlan0 is up, I can't reach any host with either interface (even nameservers or the gateway I am supposedly connected to).  ifconfig indicates that nothing is wrong.  It's really not clear what is causing this problem.  It seems like something has to be wrong with both the wireless hardware/drivers and the routing tables in order for turning wireless on to interfere with "ping -Ieth0".

[quote=ifconfig]eth0      Link encap:Ethernet  HWaddr 00:07:e9:a9:08:fe
          inet addr:18.243.2.132  Bcast:18.243.255.255  Mask:255.255.0.0
          inet6 addr: fe80::207:e9ff:fea9:8fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:483828 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55721 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:160835073 (160.8 MB)  TX bytes:4651060 (4.6 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:18140 (18.1 KB)  TX bytes:18140 (18.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:2d:3e:e8:c0
          inet addr:18.111.69.222  Bcast:18.111.95.255  Mask:255.255.224.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:331307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:813 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:39435947 (39.4 MB)  TX bytes:106301 (106.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-2D-3E-E8-C0-00-00-00-00-00-00-00-00-00-00
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/quote]

[quote=interfaces]
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 18.243.2.132
        netmask 255.255.0.0
        gateway 18.243.0.1

iface wlan0 inet static
        address 18.111.69.222
        netmask 255.255.224.0
        gateway 18.111.64.1

[/quote]
[quote=rt_tables]
#
# reserved values
#
255     local
254     main
253     default
0       unspec
#
# local
#
#1      inr.ruhep

# tldp.org/HOWTO/Adv-Routing-HOWTO/lartc.rpdb.multiple-links.html

ip route add 18.111.64.0        dev wlan0       src 18.111.69.222       table T1
ip route add default via 18.111.64.1    table T1
ip route add 18.243.0.0         dev eth0        src 18.243.2.132        table T2
ip route add default via 18.243.0.1     table T2

ip route add 18.111.64.0        dev wlan0       src 18.111.69.222
ip route add 18.243.0.0         dev eth0        src 18.243.2.132

ip route add default via 18.111.64.1

ip rule add from 18.111.69.222  table T1
ip rule add from 18.243.2.132   table T2
[/quote]

One last interesting piece of information is that the server accepts incoming connections (e.g. ssh) on wired even when the wireless is up, but only from a machine on the same ethernet switch.

Any ideas?

---

### Post by Iowan on 2010-03-30
Ordinarily, you only specify one (default) gateway. That's where everything not slated for a specific place should go. You can (should) set up a _route_ for the "alternate" interface, though.

---

### Post by nhk on 2010-03-31
I tried commenting out "gateway 18.111.64.1".  eth0 now works, but wlan0 doesn't.

---

### Post by RyanRahl on 2010-03-31
what gateway are you using on your client? maybe you should only have one gateway for the server and use the server as a router for the rest of your network.

---

### Post by nhk on 2010-04-01
Sorry, I don't see how that relates to my situation.  I need this host to have access to two networks; I know this can be done as it was working when I was using Debian.

---

### Post by Iowan on 2010-04-01
I'm not at all familiar with **rt_tables**.
If wireless is the default link, does it work if you use that as a gateway instead? (Probably off-topic, but I noticed wlan0 isn't configured for "auto")

---

### Post by nhk on 2010-04-02
If I comment out the wired gateway instead, nothing works, even if only one interface is up.

---

### Post by Iowan on 2010-04-02
> **nhk said:**
> If I comment out the wired gateway instead, nothing works, even if only one interface is up.Hmmm... that would seem to be the wrong way to do things.:-k
You can check results of **route -n** with each combination. You can also try the **route add** option. Dunno if it'll conflict with what you already have in place...

---

### Post by nhk on 2010-04-05
I get this in all cases:

> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
18.111.96.0     0.0.0.0         255.255.224.0   U     0      0        0 wlan0
18.243.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         18.111.96.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         18.243.0.1      0.0.0.0         UG    100    0        0 eth0

---

### Post by nhk on 2010-04-10
Bump, any ideas?

---

