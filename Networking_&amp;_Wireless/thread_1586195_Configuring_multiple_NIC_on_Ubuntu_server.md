---
title: "Configuring multiple NIC on Ubuntu server"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by mganapa on 2010-10-01
Hello All, 
I have multiple servers in my environment. Two of them are assembled (no specific manufacturer) and the other is a 4U rackmount IBM x-Series server. The first two servers have the 2 Dlink DGE gigabit-560T PCIe adapters and the IBM has one Intel® PRO/1000 MT Dual Port Server Adapter. So in all the 3 systems I have there are atleast 2 gigabit ethernet interfaces and one 100 MBps interfaces.
Each of these are configured in /etc/networking/interfaces file with manual IP address. Typical configuration for an interface is 
```

auto eth-n
iface eth-n inet static
    address 192.168.0.xx
    network 192.168.0.0
    netmask 255.255.255.0
    broadcast 192.168.0.255
    gateway 192.168.0.1

``` 
The issue is that when the system is rebooted, I am not able to connect to any of these machines, I cannot ping the network from these machines; ie. the systems are isolated from the network. 
Once I execute "route add default gw 192.168.0.1" from shell as route, the systems are connected to the network. 
 
I have done the following. 
1. Remove the gateway line from the config and replace it with ```
post-up route add default gw 192.168.0.1
```
 
2. Include the device to be assigned to the default gw (```
post-up route add default gw 192.168.1.200 dev eth0
```)
 
Output of route -n
```
 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0        U     0       0        0 eth0
192.168.0.0     *               255.255.255.0        U     0       0        0 eth1
192.168.0.0     *               255.255.255.0        U     0       0        0 eth2
default         192.168.0.1       0.0.0.0            UG    100     0        0 eth0

```
 
3. Define the default gateway for every interface. 
 
Output of route -n
```
 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0        U     0       0        0 eth0
192.168.0.0     *               255.255.255.0        U     0       0        0 eth1
192.168.0.0     *               255.255.255.0        U     0       0        0 eth2
default         192.168.0.1       0.0.0.0            UG    100     0        0 eth0
default         192.168.0.1       0.0.0.0            UG    100     0        0 eth1
default         192.168.0.1       0.0.0.0            UG    100     0        0 eth2

```
4. Define the default gateway for only one interface. 
 
Output of route -n
```
 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0        U     0       0        0 eth0
192.168.0.0     *               255.255.255.0        U     0       0        0 eth1
192.168.0.0     *               255.255.255.0        U     0       0        0 eth2
default         192.168.0.1       0.0.0.0            UG    100     0        0 eth2

```
 
None of these configurations work. No matter what after a reboot, I have to execute 
```
route add default gw 192.168.0.1
``` to have an active network connection. 
 
 
As for the server information, I have ubuntu 10.04 64bit on the two assembled machined and Ubuntu 10.04 32-bit on IBM server. Any help on configuring multiple interfaces would be great.

---

### Post by SeijiSensei on 2010-10-01
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0        U     0       0        0 eth0
192.168.0.0     *               255.255.255.0        U     0       0        0 eth1
192.168.0.0     *               255.255.255.0        U     0       0        0 eth2
default         192.168.0.1       0.0.0.0            UG    100     0        0 eth2

```


You need different IP subnets on the various interfaces.  As it stands now, the machine doesn't know which interface to use when it has a packet destined for a machine in 192.168.0.0/24.

Only one interface should be in 192.168.0.0/24, presumably the one that connects to other machines in the same address space.  Assign the other interfaces to other address blocks like 192.168.1.0/24, etc., and assign any other devices that connect to those interfaces addresses in the same spaces.

Make sure IP forwarding is enabled in the kernel as well.  Check /etc/sysctl.conf and see if "net.ipv4.ip_forward" is set to one.  If not, you'll need to fix that and reboot.

---

### Post by Iowan on 2010-10-01
What are the results of **route -n** after you add the default gateway? Are the NICS all in the same subnet (192.168.0.X)? If so, I'm surprised it works.

---

### Post by mganapa on 2010-12-15
Could anyone tell me the specific configuration I should use to have the two NIC's on different subnets? I connect these to a 24-port switch which is connected to a router. I am not too good with networking (obvious).

---

