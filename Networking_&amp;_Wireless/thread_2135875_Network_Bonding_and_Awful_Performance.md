---
title: "Network Bonding and Awful Performance"
date: 2013-04-15
forum: Networking &amp; Wireless
---

### Post by erisium on 2013-04-15
Greetings,
I've been tasked with setting up an iSCSI mounted Storage Area Network (SAN), which I was thought was pretty simple. I am posting  here because I am a bit dumbfounded with the Synology RS10613xs+  NAS/SAN. The link and product information for those that are not  familiar with this model is here: [http://www.synology.com/products/produc ... 2B&lang=us]("http://www.synology.com/products/product.php?product_name=RS10613xs%2B&lang=us") . 

The  RackStation is populated with 3TB 6Gb/s 7200rpm WD3001FYYG-01SL3 drives  for a total of 21TiB storage, 2 Intel 480GB SSDs for cache, and is  connected to a server running Ubuntu 10.04.2 using 10GBE Intel X520-SR2  on both the Linux and Synology boxes with appropriate fibre cables  connecting them directly. Synology NAS is running DSM4.1-2851. Both  10GBE NICs are bonded using balanced-rr mode, theoretically providing  20GBE connections to one another (I realise this will not be achieved). Each 10GBE NIC has two ports on it, so port trunking would be ideal to get the best throughput and reliability. A block-level LUN has been  created and mounted using Open iSCSI. 

Now, I would expect decent  speeds from this configuration. Transferring a 18GB file between the  LINUX server and the NAS, however, is done at a rate of ~60MB/s  (480Mb/s). I have measured this multiple times using iftop and dstat looking  at the bonded interface (bond0) and eth2 and eth3 adaptors (a single NIC, but two physically separate fibre channel ports). I find that **_exceptionally slow_**  for the hardware involved. Achieving approximately 10% of theoretical  bandwidth capacity is awful. I have poured over the Ubuntu configuration  files, help files, and Synology help files regarding configuration of Ubuntu, but have not come across anything that has mentioned issues like  this. As of now, I have even managed to completely mess over the networking configuration files and am need of help. 

Here are my configuration files for*** Ubuntu 10.04.2 Server LTS***:

 ***/etc/network/interfaces*:** (all x's in place of IP quads are the same).
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback

#-- SSH CONNECTION; DO NOT ALTER --#
auto eth1
iface eth1 inet dhcp

#-- INTEL X520-SR2 CONFIG --#
auto eth2
        iface eth2 inet static
        address x.x.x.12
        gateway x.x.x.0

auto eth3
        iface eth3 inet static
        address x.x.x.13
        gateway x.x.x.0

auto bond0
        iface bond0 inet static
        bond-miimon 100
        bond-mode 0
        address  x.x.x.15
        gateway x.x.x.0
        netmask  255.255.255.0
        slaves eth2 eth3

        up ifenslave bond0 eth2 eth3
        down ifenslave -d bond0 eth2 eth3

```

[B]/etc/modprobe.d/aliases.conf
[/B]```
alias bond0 bonding
options bonding mode=0 miimon=100 downdelay=200 updelay=200

```

***/etc/sysctl.conf ***
I added the following lines to an otherwise untouched sysctl.conf file: 
```
# -- 10GBE  BONDED ETHERNET TUNING -- #
# Increase system file descriptor limit
#fs.file-max = 65535

# Increase system IP port range to allow for more concurrent connections
#net.ipv4.ip_local_port_range = 1024 65000

# -- 10gbe tuning from Intel ixgb driver README -- #

# turn off selective ACK and timestamps
#net.ipv4.tcp_sack = 0
#net.ipv4.tcp_timestamps = 0

# memory allocation min/pressure/max.
# read buffer, write buffer, and buffer space
#net.ipv4.tcp_rmem = 10000000 10000000 10000000
#net.ipv4.tcp_wmem = 10000000 10000000 10000000
#net.ipv4.tcp_mem = 10000000 10000000 10000000

#net.core.rmem_max = 524287
#net.core.wmem_max = 524287
#net.core.rmem_default = 524287
#net.core.wmem_default = 524287
#net.core.optmem_max = 524287
#net.core.netdev_max_backlog = 300000


```

Using *ifup eth2 eth3 *, I now get:
```
Don't seem to be have all the variables for eth2/inet.
Failed to bring up eth2.
Don't seem to be have all the variables for eth3/inet.
Failed to bring up eth3.
Don't seem to be have all the variables for bond0/inet.
Failed to bring up eth3
```

Verification that the NICs are at least detecting was done with *ethtool* ([I]sudo ethtool -i eth2)
[/I]```

**eth2**
driver: ixgbe
version: 2.0.44-k2
firmware-version: 0.9-3
bus-info: 0000:05:00.0

**eth3**
driver: ixgbe
version: 2.0.44-k2
firmware-version: 0.9-3
bus-info: 0000:05:00.1

```

I have come into this project after previous configurations were setup (installation of Ubuntu 10.04.2, some minor installation of software, etc). I noticed that Webmin 1.620 has been installed to make it easier for some to access management commands and have noticed that errors often pop up when dealing with bond0, eth2, and eth3. Could there be some conflict here? I've been doing all of my work through SSH terminal sessions.

The network interfaces used to work (not sure why they aren't anymore to be honest--help?), is there anything that I need to be doing differently? I've been using ifenslave 2.6 (1.1.0.15ubuntu) from launchpad and whatever the latest package for open-iscsi. Would upgrading to 12.10 LTS be advised? Other thoughts or suggestions? Any help is appreciated. I've got to get these talking again so I can at least have the 60MB/s iSCSI connection; I just wanted to get better speeds than that considering the hefty price tag all of these components.

Cheers

---

### Post by erisium on 2013-04-15
So, I made a derp mistake and corrected my */etc/network/interfaces *file to get eth2 and eth3 working again. See the configuration below now. 
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# CONNECTION TO SERVER VIA FACILITIES NETWORK--DO NOT CHANGE
auto eth1
iface eth1 inet dhcp

# 10GBE configuration BELOW
auto eth2
        iface eth2 inet static
        address 10.10.20.12
        **network 10.10.20.0**
        netmask 255.255.255.0

auto eth3
        iface eth3 inet static
        address 10.10.20.13
       ** network 10.10.20.0**
        netmask 255.255.255.0

auto bond0
        iface bond0 inet static
        bond-miimon 100
        bond-mode 0
        address  10.10.20.15
       ** network 10.10.20.0**
        netmask  255.255.255.0
        slaves eth2 eth3

        up ifenslave bond0 eth2 eth3
        down ifenslave -d bond0 eth2 eth3


```

Here's the output from [I]ifconfig.
```
[/I]bond0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:10.10.20.15  Bcast:10.10.20.255  Mask:255.255.255.0
          inet6 addr: fe80::92e2:baff:fe38:2ae0/64 Scope:Link
          UP BROADCAST MASTER MULTICAST  MTU:9000  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr bc:ae:c5:48:50:82  
          inet addr:192.168.20.124  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: fe80::beae:c5ff:fe48:5082/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79098 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38975 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:13333962 (13.3 MB)  TX bytes:9210629 (9.2 MB)
          Memory:fbde0000-fbe00000 

eth2      Link encap:Ethernet  HWaddr 90:e2:ba:38:2a:e0  
          inet addr:10.10.20.12  Bcast:10.10.20.255  Mask:255.255.255.0
          inet6 addr: fe80::92e2:baff:fe38:2ae0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:9000  Metric:1
          RX packets:587 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:100302 (100.3 KB)  TX bytes:3729730 (3.7 MB)

eth3      Link encap:Ethernet  HWaddr 90:e2:ba:38:2a:e1  
          inet addr:10.10.20.13  Bcast:10.10.20.255  Mask:255.255.255.0
          inet6 addr: fe80::92e2:baff:fe38:2ae1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:9000  Metric:1
          RX packets:2452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2034 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1893948 (1.8 MB)  TX bytes:3175560 (3.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:269 errors:0 dropped:0 overruns:0 frame:0
          TX packets:269 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22890 (22.8 KB)  TX bytes:22890 (22.8 KB)

virbr0    Link encap:Ethernet  HWaddr 7a:c9:94:14:8c:d7  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::78c9:94ff:fe14:8cd7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:27281 (27.2 KB)

[I]
```
[/I]```
[CODE]
```[/CODE]

---

