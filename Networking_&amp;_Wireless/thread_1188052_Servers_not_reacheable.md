---
title: "Servers not reacheable"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by LazzariAngelo on 2009-06-15
Hello,
i have this situation:
Server A (Static IP X, internal IP X_int)
Server B (Static IP Y, internal IP Y_int)

after a reboot (yesterday morning) the ping from X_int to Y_int doesn't work, but no network setting modified before last reboot.

i had mysql master/slave connection between the 2 server (linked with the internal IP), but now mysql can't reach the master Ip X_int).

Are there any setting that i havo to do automatically when server reboot?

Thank you
Angelo

---

### Post by superprash2003 on 2009-06-15
are those internal static ips?? have you done an ifconfig to check if the ips are still there..

---

### Post by Iowan on 2009-06-15
What is in your */etc/network/interfaces*?

---

### Post by LazzariAngelo on 2009-06-16
Hi,
my ifconfig -a returns on the server X:
eth0      Link encap:Ethernet  HWaddr 00:15:17:8f:0f:ea
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0xdcc0 Memory:dfc80000-dfca0000

eth1      Link encap:Ethernet  HWaddr 00:15:17:8f:0f:eb
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0xdce0 Memory:dfcc0000-dfce0000

eth2      Link encap:Ethernet  HWaddr 00:22:19:b2:61:b7
          inet addr:192.168.102.4  Bcast:192.168.102.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28382 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32782 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3316876 (3.1 MB)  TX bytes:5622249 (5.3 MB)
          Interrupt:16

eth3      Link encap:Ethernet  HWaddr 00:22:19:b2:61:b8
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7764 (7.5 KB)  TX bytes:7764 (7.5 KB)


and his interfaces:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet static
        address 192.168.102.4
        netmask 255.255.255.0
        gateway 192.168.102.1


and on the server Y:
eth0      Link encap:Ethernet  HWaddr 00:1C:23:E3:0A:FC
          inet addr:192.168.102.2  Bcast:192.168.102.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fee3:afc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:520326 errors:0 dropped:0 overruns:0 frame:0
          TX packets:592016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:80111273 (76.4 MB)  TX bytes:331695419 (316.3 MB)
          Interrupt:16

eth1      Link encap:Ethernet  HWaddr 00:1C:23:E3:0A:FD
          inet addr:192.168.102.3  Bcast:192.168.102.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4561418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4561418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2195304080 (2.0 GB)  TX bytes:2195304080 (2.0 GB)

and his interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.102.2
        netmask 255.255.255.0
        gateway 192.168.102.1

auto eth1
iface eth1 inet static
        address 192.168.102.3
        netmask 255.255.255.0
        gateway 192.168.102.1


the two internal can login previous week but after the reboot of last sunday they cannot. :(

thx!

---

### Post by superprash2003 on 2009-06-16
you could try bringing down the other interfaces which are not being used , by using the ifdown command , for example : to bring down eth0 type sudo ifdown eth0 

 also post output of route -n

---

### Post by LazzariAngelo on 2009-06-16
Hi,
all the eth not used are down.

Here is my route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.102.0   0.0.0.0         255.255.255.0   U     0      0        0 eth2
0.0.0.0         192.168.102.1   0.0.0.0         UG    100    0        0 eth2

Thx!

---

### Post by jhannah on 2009-06-17
What does the output of route -n look like on the second server and how are these servers physically cabled up?

From what I see, there are two interfaces in the same network on the second server which are both up in the 192.168.102.0/24 network. These would both need to be cabled to the same physical network but it sounds mostly superfluous to do that as you could simply use a single physical interface with an aliased IP address (should you need more than one IP on that machine). Depending on how it is cabled and what exactly you need, you could also probably get away with renumbering one of those networks so it falls under a separate network in RFC-1918 space (ie 192.168.103.0/24).

---

