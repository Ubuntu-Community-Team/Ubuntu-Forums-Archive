---
title: "KVM/QEMU Bridged Networking Problem"
date: 2011-07-02
forum: Networking &amp; Wireless
---

### Post by gus_zernial on 2011-07-02
I have been running Win7 under KVM/QEMU. After upgrading to
Kubuntu 11.04 something has changed so that my Win7 client
bridged networking no longer works.

My /etc/network/interfaces and ifconfig output are below. The
ifconfig shows an eth1 getting an IP address by DHCP while the
/etc/network/interfaces is configured for a static address. 

-Where is the primary ethernet interface configured to use DHCP?
(Apparently not in /etc/network/interfaces)

-Where did virbr0 come from and how is it configured? I didn't configure it


$ cat /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Configure the actual Ethernet device in promiscuous mode and
# add it to the bridge
iface eth0 inet manual
        pre-up ifconfig eth0 0.0.0.0 promisc up
        pre-up brctl addif br0 eth0
        pre-down brctl delif br0 eth0
        pre-down ifconfig eth0 down


# Create our bridge interface using a static IP address on the network
auto br0
iface br0 inet static
        address 192.168.1.17
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        pre-up ifconfig eth0 down
        pre-up ifconfig eth0 0.0.0.0 promisc up
        pre-up brctl addbr br0
        pre-up brctl addif br0 eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:30:67:74:87:d1  
          inet addr:192.168.1.118  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:67ff:fe74:87d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5633 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3011820 (3.0 MB)  TX bytes:786062 (786.0 KB)
          Interrupt:42 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2180 (2.1 KB)  TX bytes:2180 (2.1 KB)

virbr0    Link encap:Ethernet  HWaddr b2:6f:00:08:a3:eb  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:13522 (13.5 KB)

---

