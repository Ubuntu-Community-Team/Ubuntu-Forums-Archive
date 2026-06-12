---
title: "ubuntu 11.04 Ethernet bonding 802.3ad aggregation issue"
date: 2011-11-16
forum: Networking &amp; Wireless
---

### Post by mdfakkeer on 2011-11-16
Hi guys,
 
I have a question about ethernet bonding 802.3ad and the switches they are connected to. If I am wrong in any of my assumptions, please correct me.
 
I have a ubuntu 11.04 64 bit server which needs to send a lot of data to another ubuntu 11.04 server quickly. Both have multiple GbE NICs. I understand what is required at the server end (I think) in that a pseudo-interface is created such as bond0 with the IP applied to that interface rather than eth0 and eth1.
 
What I am trying to work out is if I had a storage server connected to an application server and exporting storage using NFS or GlusterFS, would an aggregated link improve throughput?
 
i configured ifenslave and ethernet bonding as per ubuntu official documentation
 
i am using netgear GS724T switch which has LACP facility. I configured LAG as per switch document.
 
please find the network configuration for the both servers
 
nodeadmin@node101:~$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
#auto eth0
#iface eth0 inet static
&#12288;
&#12288;
auto ceph0
iface ceph0 inet static
address 10.1.1.101
netmask 255.255.248.0
bond-slaves eth0 eth1
bond_mode 802.3ad
bond_miimon 100
bond_lacp_rate 1
&#12288;
&#12288;
nodeadmin@node102:~$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
#auto eth0
#iface eth0 inet static
auto ceph0
iface ceph0 inet static
address 10.1.1.102
netmask 255.255.248.0
bond-slaves eth0 eth1
bond_mode 802.3ad
bond_miimon 100
bond_lacp_rate 1
&#12288;
&#12288;
i checked the bonding interface of the both the servers. it shows bonding is working fine.
 
 
nodeadmin@node102:~$ cat /proc/net/bonding/ceph0 
Ethernet Channel Bonding Driver: v3.7.0 (June 2, 2010)
Bonding Mode: IEEE 802.3ad Dynamic link aggregation
Transmit Hash Policy: layer2 (0)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0
802.3ad info
LACP rate: fast
Aggregator selection policy (ad_select): stable
Active Aggregator Info:
Aggregator ID: 9
Number of ports: 2
Actor Key: 17
Partner Key: 53
Partner Mac Address: a0:21:b7:97:4b:7f
Slave Interface: eth0
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 00:e0:81:c8:c7:41
Aggregator ID: 9
Slave queue ID: 0
Slave Interface: eth1
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 00:e0:81:c8:c7:42
Aggregator ID: 9
Slave queue ID: 0
 
 
nodeadmin@node101:~$ cat /proc/net/bonding/ceph0 
Ethernet Channel Bonding Driver: v3.7.0 (June 2, 2010)
Bonding Mode: IEEE 802.3ad Dynamic link aggregation
Transmit Hash Policy: layer2 (0)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0
802.3ad info
LACP rate: fast
Aggregator selection policy (ad_select): stable
Active Aggregator Info:
Aggregator ID: 9
Number of ports: 2
Actor Key: 17
Partner Key: 52
Partner Mac Address: a0:21:b7:97:4b:7f
Slave Interface: eth0
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 00:e0:81:c8:ca:e8
Aggregator ID: 9
Slave queue ID: 0
Slave Interface: eth1
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 00:e0:81:c8:ca:e9
Aggregator ID: 9
Slave queue ID: 0
&#12288;
&#12288;
 
my question is when i check the throughput between two servers it is showing as single interface throughput. it means it is showing 943Mbps. why link aggregation is not happened? The switch showing LACP interface link is UP. Help will be appreciated.

---

### Post by spynappels on 2011-11-16
Howdy,

For 2 aggregated GbE links, getting nearly 1 GbE actual throughput is pretty good I would have thought. What throughput were you expecting to get?

---

### Post by mdfakkeer on 2011-11-16
without link aggregation normally i got 950 Mbps with single ethernet cable. i required 2 gbps throughput .

---

### Post by mdfakkeer on 2011-11-22
In switch port 0/1 and 0/2 used for system1 and port 0/3 and 0/4 used for system2. port0/1 and 0/2 is aggregated and port0/3 and 0/4 is aggregated in switch.
 
i checked indual port throughput in switch
 
When i am configured LACP 802.3ad in system with xmit hash value as Layer2 one ethernet interface have the traffic other one is idle. please see the attachment
 
Also i changed to xmit hash value as layer2+3. Now Each system using one ethernet for sending packets and one ethernet for receiving packets. Please see the attachment layer2+3.png
 
Mode4( 802.3ad ) gives only 112MB/s throughput between system1 and system2. I changed all xmit hash value but still i am getting 112 MB/s Throughput.
 
when i changed to mode0 roundrobin Method, Both ethernet interface fully utilized and giving 200MB/s throughput. Please see the attachment for the mode0 throughput in mode0.png
 
 
I dont know where i made mistake. Why 802.3d not giving high throughput? If any bug is available in mode4( 802.3ad)?
 
if any body know about this issue plese help me.

---

### Post by mdfakkeer on 2011-11-25
how to integrate two 1 Gbps ethernet link to one single 2gbps throughput ethernet link?. Is it possible in linux? Help will be appreciated.

---

