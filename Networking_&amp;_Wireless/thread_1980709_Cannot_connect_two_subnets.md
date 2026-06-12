---
title: "Cannot connect two subnets"
date: 2012-05-15
forum: Networking &amp; Wireless
---

### Post by lloowen on 2012-05-15
This has been bothering me for a couple of days,

I have two subnets:

192.168.1.0/24 : This is the subnet used by my ISP/router. The gateway to the WAN is 192.168.1.1
192.168.2.0/24 : This is a subnet that I've created on my ESXi 5 virtual machine.

The physical machine that ESXi 5 is running on has two NIC's one NIC is connected to my ISP/router and the other is connected to another router with the DHCP server disabled. I'm using this second router just to keep the NIC status 'UP' from a vmware perspective.

I have a virtual Ubuntu 10.04 LTS running with two NIC's connected to it. The idea is that this will serve as a router between the two subnets. I have DHCP running on the Ubuntu router that is dishing out IPs to my virtual machines using the 192.168.2.0 LAN.

The problem I'm having is that I can't seem to get the Ubuntu router to forward packets from one subnet to another. I should note I have tried every possible combination of configuration settings I can think of. My current set up is as follows:


I have run the command 'echo 1 > /proc/sys/net/ipv4/ip_forward' to enable packet forwarding.


My firewall looks like this:

root@gRouter:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination



My '/etc/network/interfaces' looks like this:

root@gRouter:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo eth0 eth1
iface lo inet loopback

iface eth0 inet static
        address 192.168.1.105
        network 192.168.1.0
        netmask 255.255.255.0
        up ip route add 192.168.2.0/24 via 192.168.1.105


iface eth1 inet static
        address 192.168.2.2
        network 192.168.2.0
        netmask 255.255.255.0
        up ip route add 192.168.1.0/24 via 192.168.2.2

From this dual NIC router to be, I can ping between virtual machines within the 192.168.2.0 subnet and I can ping between virtual machines and physical machines on the 192.168.1.0 subnet. But I cannot ping from one subnet to another.


My routes table looks like this:

root@gRouter:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0


My arp currently looks like this:

root@gRouter:~# arp -v
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.2.13             ether   00:0c:29:30:f4:d9   C                     eth1
192.168.2.10             ether   00:0c:29:bf:60:a3   C                     eth1
192.168.1.64             ether   38:59:f9:e7:a0:f5   C                     eth0
Entries: 3      Skipped: 0      Found: 3

When I try to ping from a machine in subnet 192.168.2.0 to a machine in 192.168.1.0 subnet, I immediately get the error message 'connect: Network is unreachable'

When I try to ping from a machine in subnet 192.168.1.0 to a machine in 192.168.2.0 subnet, the first ping is initiated but it just hangs indefinately.

Sorry for the long post, I hope I have given enough information. Really grateful for any help.

Thanks in advance.

---

### Post by sanajeya on 2012-09-02
Somebody!!!!! 
Help Please I have exactly the same problem too.. it's been 48 hours straight no sleep..

---

