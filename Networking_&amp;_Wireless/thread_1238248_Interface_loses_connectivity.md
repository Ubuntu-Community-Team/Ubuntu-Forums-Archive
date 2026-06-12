---
title: "Interface loses connectivity"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by joec22 on 2009-08-12
I've setup an iscsi storage server.  Everything was working fine, but then the second interface I have connected to the storage network lost its connection.  I could not ping this interface from the client machine until I attempted from the server to ping the client.

Here is the ip configuration - the storage subnet is on eth1:
```
sudo cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# auto eth0
# iface eth0 inet dhcp

auto eth0
iface eth0 inet static
	address 192.168.20.41
	netmask 255.255.255.0
	broadcast 192.168.20.255
	network 192.168.20.0
	gateway 192.168.20.2

auto eth1
iface eth1 inet static
	address 192.168.80.41
	netmask 255.255.255.0
	broadcast 192.168.80.255
	network 192.168.80.0
```

Here is the routing:
```
sudo netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.20.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.80.0    0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         192.168.20.2    0.0.0.0         UG        0 0          0 eth0
```

Are there any logs I can check to see why it may have lost connection?  It seems like a routing problem, but I think I have the interfaces correct.  Any ideas?

Thanks

---

### Post by superprash2003 on 2009-08-12
did you try restarting networking?

---

### Post by joec22 on 2009-08-12
since the eth1 connection started working once i pinged a client on the 80 subnet from the server, restarting networking wouldn't prevent a future disconnect.  i'm looking for a suggestion that will prevent this from happening in the future.

---

### Post by joec22 on 2009-08-12
I have some more information, although not solved yet.

From ubuntu, arp result
```
sudo arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.20.91            ether   00:15:5d:14:97:03   C                     eth0
192.168.80.78                    (incomplete)                              eth1
192.168.20.2             ether   00:14:69:64:87:41   C                     eth0
192.168.20.1             ether   00:12:7f:f5:02:3c   C                     eth0

```

A similar arp command on the windows client displayed all 0's for the HWaddress, and type invalid.  I'm not sure if this info helps...

---

### Post by joec22 on 2009-08-24
Update - I believe I have found the issue.  I noticed that the windows client was using the provide Microsoft drivers for the network card.  I updated those to the correct intel drivers, and have not lost connectivity to the iscsi targets since.

---

### Post by joec22 on 2009-08-31
Correction, this is not solved.  I thought it was the drivers, because it worked for almost 2 weeks.  But it has lost connection twice in the last 3 days.  I don't know what the problem is.

---

### Post by joec22 on 2009-10-08
I have discovered a correlation between losing network connectivity and high cpu usage.  This is a storage server used as backup.  It hosts iscsi targets.  I copy data throughout the day, and perform backups at night all to the iscsi clients using this server's volumes.  

During consistent read and write activities, the quad-core cpu utilization has been as high as 50%.  During this time the network connection tends to be problematic.  Either the iscsi connection for the clients disconnects momentarily, or the interface becomes unreachable until I ping a client on the same subnet.  Both interfaces are on the board.

Memory (4GB) does not seem to be an issue at all.  More than 3GB are unused.

---

