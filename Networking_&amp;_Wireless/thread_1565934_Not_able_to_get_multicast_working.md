---
title: "Not able to get multicast working"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by ndoggac on 2010-09-01
I have several multicast data feeds that I'm trying to connect to using a minimal server install of Ubuntu as a VM on a VMWare ESXi server.

I have another VM on the same server running Solaris that can connect with no issues to the incoming multicast stream.  All I had to do on the Solaris machine was run:

route -p add 224.0.0.0/4 -iface 10.54.1.157
then
snoop -r -d e1000g2 udp | grep 225.   (or grep 224.)
in order to see the incoming data

On the Ubuntu server VM I tried doing the same thing and making it persistent by adding the following to /etc/network/interfaces:

post-up route add -net 224.0.0.0/4 gw 10.54.1.6 dev eth1
also tried
post-up route add -net 224.0.0.0/4 dev eth1

Result of netstat -rnv
---------------------
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.54.1.0       0.0.0.0         255.255.255.0   U         0 0          0 eth1
172.26.190.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0
224.0.0.0       10.54.1.6       240.0.0.0       UG        0 0          0 eth1
0.0.0.0         172.26.190.254  0.0.0.0         UG        0 0          0 eth0
---------------------

The only difference when I tried the two different entries was the gateway flag disappearing and the gateway going to 0.0.0.0
I rebooted after each attempt.

Still not able to see any multicast data on that interface using 

tcpdump -v -i eth1

or using wireshark for that interface.


/etc/network/interfaces File:
---------------------
# The loopback network interface
auto lo eth0 eth1
iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address 172.26.190.157
        netmask 255.255.255.0
        network 172.26.190.0
        broadcast 172.26.190.255
        dns-nameservers 172.26.190.150
        dns-search nstb.act.faa.gov
        gateway 172.26.190.254
        # dns-* options are implemented by the resolvconf package, if installed


iface eth1 inet static
        address 10.54.1.6
        netmask 255.255.255.0
        broadcast 10.54.1.255
        network 10.54.1.0
        post-up route add -net 224.0.0.0/4 gw 10.54.1.6 dev eth1
---------------------

All the multicast data comes in on eth1.
Any help would be appreciated!

---

### Post by purple_minion on 2010-10-09
I'm currently playing with IPTV and multicast and found you need to disable the reverse packet filter by 

echo 0 > /proc/sys/net/ipv4/conf/all/rp_filter
echo 0 > /proc/sys/net/ipv4/conf/ethX/rp_filter

where ethX is the interface you want to receive on. Not sure if you need to do both all and ethX but I had to in order to get VLC and mythtv to see anything.
You can change the default boot up values in /etc/sysctl.conf

---

