---
title: "can't connect to the internet local ok"
date: 2010-12-18
forum: Networking &amp; Wireless
---

### Post by DanYoSon on 2010-12-18
Hi
i have a server running ubuntu 10.04 64bit and am having a weird problem, i can ssh the box and it can ping the other computers on the network, but i can not access anything outside the network. i don't believe that it is a dns issue because even if i ping the ip address of Google it still does not work. the rest of the computers on the network and even the virtual machine that is running on this box, using the bridge interface, works. 

Here is some debug info i have seen other people asking for but it all looks ok to me.

output of:
```
~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 br0
default         192.168.1.1     0.0.0.0         UG    100    0        0 br0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth1

```
this looks normal to me


interfaces file
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 192.168.1.52
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

auto eth1
iface eth1 inet static
        address 192.168.1.51
        netmask 255.255.255.0
        gateway 192.168.1.1

```

now i am wondering what other things i should check and where i should go from here.

---

### Post by xirochanh on 2010-12-29
I got the same problem with you, don't know why

---

### Post by cracker89 on 2010-12-29
I had a problem like that. Check your proxy settings... can you access any other site at all?
try that..

---

### Post by xirochanh on 2010-12-29
I solved this issue by commenting out the gateway on eth1 because eth1 is on same subnet with eth0(should be different), and also in /etc/resolv.conf put the dns as:
nameserver 192.168.1.1

---

