---
title: "Unable to ping via ETH0, but connected via ETH0"
date: 2013-04-04
forum: Networking &amp; Wireless
---

### Post by ub-newbie on 2013-04-04
UB Server 12.04.  Router is 192.168.4.1
abreviated: ```
root@Server900:/home/user# iptables -L -n
Chain INPUT (policy ACCEPT)
Chain FORWARD (policy ACCEPT)
Chain OUTPUT (policy ACCEPT)

```
```
root@Server900:/home/user# ufw status
Status: inactive

```
```
root@Server900:/home/user# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:48:**:**:11
          inet addr:192.168.4.27  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::280:48ff:fed3:611/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0xe000 Memory:df000000-df020000

eth1      Link encap:Ethernet  HWaddr 00:10:4b:**:**:05
          inet addr:192.168.4.41  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::210:4bff:fe9a:3305/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1255 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:218557 (218.5 KB)  TX bytes:1950 (1.9 KB)
          Interrupt:5 Base address:0xa000

eth2      Link encap:Ethernet  HWaddr 00:80:48:**:**:05
          inet addr:192.168.4.42  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::280:48ff:fed3:605/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xe400 Memory:df002000-df022000

eth3      Link encap:Ethernet  HWaddr 00:80:48:**:**:28
          inet addr:192.168.4.43  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::280:48ff:fed3:628/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xe800 Memory:df004000-df024000

eth4      Link encap:Ethernet  HWaddr 08:00:09:**:**:89
          inet addr:192.168.4.44  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:9ff:fefa:df89/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4178 errors:1 dropped:0 overruns:0 frame:0
          TX packets:3343 errors:403 dropped:0 overruns:0 carrier:402
          collisions:0 txqueuelen:1000
          RX bytes:530816 (530.8 KB)  TX bytes:472199 (472.1 KB)
          Interrupt:11 Base address:0xec00 DMA chan:4

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:145 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13727 (13.7 KB)  TX bytes:13727 (13.7 KB)

```

/etc/network/interfaces

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.4.27
netmask 255.255.255.0
gateway 192.168.4.1
broadcast 192.168.4.255
network 192.168.4.0
dns-nameservers 8.8.8.8 208.67.222.222


auto eth1
iface eth1 inet static
address 192.168.4.41
netmask 255.255.255.0
gateway 192.168.4.1
broadcast 192.168.4.255
network 192.168.4.0
dns-nameservers 8.8.8.8 208.67.222.222

auto eth2
iface eth2 inet static
address 192.168.4.42
netmask 255.255.255.0
gateway 192.168.4.1
broadcast 192.168.4.255
network 192.168.4.0
dns-nameservers 8.8.8.8 208.67.222.222

auto eth3
iface eth3 inet static
address 192.168.4.43
netmask 255.255.255.0
gateway 192.168.4.1
broadcast 192.168.4.255
network 192.168.4.0
dns-nameservers 8.8.8.8 208.67.222.222

auto eth4
iface eth4 inet static
address 192.168.4.44
netmask 255.255.255.0
gateway 192.168.4.1
broadcast 192.168.4.255
network 192.168.4.0

```

I am SSH'd in to 192.168.4.27 (ETH0) from Win Box (using IP, not name) 
```
netstat eth0
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0     52 192.168.4.27:ssh        dc:2817                 ESTABLISHED
tcp        0      0 192.168.4.27:ssh        dc:2343                 ESTABLISHED

```

I have another Cat-5 plugged in to ETH4, both going to same router.  I have swapped cables.
I have rebooted multiple times.

```
 ping -I eth0 192.168.4.1
PING 192.168.4.1 (192.168.4.1) from 192.168.4.27 eth0: 56(84) bytes of data.
From 192.168.4.27 icmp_seq=1 Destination Host Unreachable

and

ping -I eth0 8.8.8.8
PING 8.8.8.8 (8.8.8.8) from 192.168.4.27 eth0: 56(84) bytes of data.
From 192.168.4.27 icmp_seq=1 Destination Host Unreachable

but 

ping -I eth0 192.168.4.27
PING 192.168.4.27 (192.168.4.27) from 192.168.4.27 eth0: 56(84) bytes of data.
64 bytes from 192.168.4.27: icmp_req=1 ttl=64 time=0.175 ms


```

Yet, ```
ping -I eth4 192.168.4.1
PING 192.168.4.1 (192.168.4.1) from 192.168.4.44 eth4: 56(84) bytes of data.
64 bytes from 192.168.4.1: icmp_req=1 ttl=64 time=3.13 ms

```

I'm lost.  Since I can connect via SSH my first thought was Firewall, but IPTables is all "allow" and UFW is off.

The "odd" thing is .  Ping to "localhost" from ETH0 and ETH4 fails when using "ping -I etc..", but "ping localhost" works.

Anyone know where I should start looking.

---

### Post by Iowan on 2013-04-04
As an experiment, try putting each interface in a separate subnet.

---

### Post by lvlint67 on 2013-04-05
Eth1 and eth4 are the only interfaces showing traffic...

Are both nics that are plugged into the router the same type of nic?

Eth1 seems to be a different type... Perhaps onboard?

Eth0 shows no traffic despite the netstat results...
________
In your interface configuration file... You May want to only specify a single gateway per subnet. Your current configuration in interfaces... I can't tell you off hand what your route looks like.

Perhaps you can post the result of:
Netstat --route
_________
What is attached to eth1?
If you get board you might try swapping the ips on eth0 and eth1....


I have no idea how you are connected to .27 when there is no traffic on that interface....

---

### Post by ub-newbie on 2013-04-05
lvlint,  Tks for the the advice.
I have 3 different models of NIC's, and all VERY old (some have 2 jacks, 1 for 10 and 1 for 100)

Route gives: ```
Kernel IP routing table
Destination     Gateway         Genmask       Flags Metric Ref    Use  Iface
default         wrt               0.0.0.0            UG    100     0         0  eth0
192.168.4.0     *               255.255.255.0   U     0         0        0   eth4
192.168.4.0     *               255.255.255.0   U     0         0        0   eth1
192.168.4.0     *               255.255.255.0   U     0         0        0   eth3
192.168.4.0     *               255.255.255.0   U     0         0        0   eth2
192.168.4.0     *               255.255.255.0   U     0         0        0   eth0

```
which I "think" is ok.

I got a little "out of band" support, which pointed me to the Win box's ARP table.  For some reason eth4 (Mac -89) is assigned to .27 in Win's ARP table.  So, I cleared Win's arp table, and now ETH0 does not work, but that I can troubleshoot.

So, Solution to stated problem was to clear Win's ARP table.  As to why Win's ARP table keeps assigning .27 to ETH4 is a whole other kettle of fish.

---

### Post by ub-newbie on 2013-04-05
For myself, and anyone searching this:

used ```
lshw |more
```
to find the NIC drivers Ubuntu was using.
Turns out 3 of the 5 NIC's are ENET 100VG4, but they are using "HP100" drivers, which seems to be OK according to [http://www.cs.fsu.edu/~baker/devices/lxr/http/source/linux/drivers/net/hp100.c?v=2.6.25.8]("http://www.cs.fsu.edu/~baker/devices/lxr/http/source/linux/drivers/net/hp100.c?v=2.6.25.8")
-------------------------------------------------------------------------------
```
dmesg | grep -e hp100 -e eth
```
shows how Ubuntu was helping me, but adding to my confusion:
```
[   22.567065] udevd[335]: renamed network interface eth0 to rename2
[   22.723464] udevd[343]: renamed network interface eth1 to eth0
[   22.730467] udevd[335]: renamed network interface rename2 to eth1

```
So, what I thought was ETH0.... the system was renaming to ETH1...

---

