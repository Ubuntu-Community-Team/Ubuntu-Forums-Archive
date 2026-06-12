---
title: "(Breezy)(Router)Interface down after reboot"
date: 2006-05-22
forum: Networking &amp; Wireless
---

### Post by B0rsuk on 2006-05-22
Hey

I already asked for help in the right topic (connection sharing howto) but got ignored. I tried to find something on ubuntu forums, but found nothing.

Breezy installer properly configured my eth0, internet connection. Using a howto I found somewhere on these forums, I made connection sharing work, and my mother's Debian has access to the internet.(through eth1).
But eth1 interface doesn't get up after reboot. I can provide as much info as necessary. I have a bit of linux knowledge but I'm occupied mostly with university/TeX/C/mysqlphpcsshtmljavascriptajaxproject now and unfortunately have no time to solve it entirely on my own. Any help is welcome.
----------------------- 

eth0 provides internet to me. eth1(192.168.0.1) forwards internet from my computer to my mother's machine (192.168.0.2)
Here's how my eth0 card is configured:
> 
eth0      Link encap:Ethernet  HWaddr 00:11:D8:1E:85:08
          inet addr:10.112.0.19  Bcast:10.112.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fe1e:8508/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3833 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7429286 (7.0 MiB)  TX bytes:665732 (650.1 KiB)
          Interrupt:22 Base address:0xa000


I set up connection sharing this way:
> ifconfig eth1 192.168.0.1
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
/etc/init.d/dnsmasq restart
dpkg-reconfigure ipmasq

The result is this:
> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
10.112.0.0      *               255.255.255.0   U     0      0        0 eth0
default         10.112.0.1      0.0.0.0         UG    0      0        0 eth0


> eth1      Link encap:Ethernet  HWaddr 00:00:21:0A:0A:55
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::200:21ff:fe0a:a55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:430275 (420.1 KiB)  TX bytes:587479 (573.7 KiB)
          Interrupt:18 Base address:0xc000



...and it works, but **the interface eth1 is down after reboot.**

I tried editing /etc/network/interfaces like this:
> 
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

# Below is my combination of debian howto and gueswork. It doesn't work:
auto eth1
iface eth1 inet static
        adress 192.168.0.1
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255


**How do I make eth1 stay up after reboot ?**

---

### Post by lst1017 on 2006-05-23
Have you checked dmesg for errors on reboot?

---

