---
title: "Multicast 12.04 server configuration. Can receive local mcast but not remote"
date: 2013-05-28
forum: Networking &amp; Wireless
---

### Post by oxoocoffee on 2013-05-28
I have fresh version of 12.04 server installed with dual nic setup with static ip's. I just moved from CentOS and I have existing application that worked on this system.
Now I am fresh to Ubuntu so perhaps I an forgetting something that needs to be enabled or disabled.

Firewall is disabled
   sudo ufw disable

when I try to send and receive data locally (eth1) on this server I can send and receive just fine. (244.0.10.10 port 10000)
But when I try to listen on eth1 again with another mcast address and port (this data is coming from remote site on eth1) I am not receiving anything.

here is my interface configuration

# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
    address 10.120.80.8
    netmask 255.255.255.0
    network 10.120.80.0
    broadcast 10.120.80.255
    gateway 10.120.80.1
    dns-nameservers 10.120.80.1


auto eth1
iface eth1 inet static
    address 10.120.70.8
    netmask 255.255.255.0
    network 10.120.70.0
    broadcast 10.120.70.255
    up route add -net 10.122.70.0/24 dev eth1
        up route add -net 10.122.18.0/24 dev eth1
        up route add -net 224.0.0.0/4 dev eth1

my current route is 

Destination     Gateway         Genmask     Flags Metric Ref    Use Iface
default         10.120.80.1   0.0.0.0            UG    100    0       0 eth0
10.122.70.0     *               255.255.255.0   U     0      0        0 eth1
10.122.18.0     *               255.255.255.0   U     0      0        0 eth1
10.120.70.0     *               255.255.255.0   U     0      0        0 eth1
10.120.80.0     *               255.255.255.0   U     0      0        0 eth0
224.0.0.0        *               240.0.0.0          U     0      0        0 eth1

Why would I not be able to receive data from remote site. I can see using tcpdump on server listening on eth1 that data is coming. As soon as I stop listening tcpdump stops printing. Start listening data comes.
But my application does return from recvfrom(). Again same listener and my test mcast second locally works bind to eth1.

I tried enabling and disabling too :  [LEFT][COLOR=#000000][FONT=Consolas]echo 0 > /proc/sys/net/ipv4/conf/eth1/rp_filter
[/FONT][/COLOR][/LEFT]
Any ideas what to try?

---

