---
title: "Advanced Network Setup for Fileserver"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by insanity54 on 2011-04-27
Hello,

I work for a small business and among other things, I'm in charge of the computers. For several months, We've been running ubuntu on our new server. It is functioning as our: [LIST]
[*]Fileserver (Samba)
[*]Quickbooks Server (Virtualbox running WinXP & Quickbooks Server)
[*]Imaging Server (FOG)
[/LIST]
We have about 8 computers that can access the internet in the office. They are also on the same network as the server so they can use Quickbooks and share files. 

There are three computers that are not connected to the internet because they have important files on them and we can't afford that they get viruses. The files are spread out all over between the three computers and we need to have a central storage location for all three computers. 

I have to connect these three computers to the Server so that they are able to have a central storage location (the server also has RAID 1)and be able to share them with the other office computers, but not be able to access the internet. I've already purchased an extra NIC for the server and set it up in ubuntu as eth1. Here is a diagram of what I need to accomplish:

[IMG]http://i55.tinypic.com/el8tow.jpg[/IMG]

Here is an output of ifconfig:

```
eth0      Link encap:Ethernet  HWaddr x:x:x:x:x:x
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: x:x:x:x:x:x/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35103024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19682243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:35058504543 (35.0 GB)  TX bytes:17607409351 (17.6 GB)
          Interrupt:28 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr x:x:x:x:x:x
          inet addr:192.168.100.2  Bcast:192.168.100.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:107134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7813187 (7.8 MB)  TX bytes:7813187 (7.8 MB)

insanity54@insane-server:~$

```

and contents of /etc/network/interfaces

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface (internet LAN)
auto eth0
iface eth0 inet static
        address 192.168.1.101
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.1

# The secondary network interface (non-internet LAN)
auto eth1
iface eth1 inet static
        address 192.168.100.2
        netmask 255.255.255.0

```

Could anyone throw me a bone as to how I can configure ubuntu to allow these three isolated computers to the server so they can share files?

---

