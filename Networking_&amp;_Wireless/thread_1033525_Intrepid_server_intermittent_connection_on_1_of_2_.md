---
title: "Intrepid server intermittent connection on 1 of 2 interfaces"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by Jayock on 2009-01-07
Odd issue.  I have my intrepid server x86_64 configured to connect to two networks, on two different subnets.  We did this to up throughput to internal workstations, while leaving it on the external lan.  It is a Dell PowerEdge server with dual port integrated NIC.  The external network connection on eth0 is intermittent, however, If I first connect to the internal address on eth1, eth0 will respond every time.  

I have a band-aid in place by setting up a `ping -c 10 internal.ip` on another internal linux workstation crontab every minute, but as soon as you stop this traffic is intermittent to eth0 once again.  Its like eth0 responds for a bit after any request goes to eth1, but then stops shortly after any periods of inactivity.

I have no ideas where to even start looking, any suggestions.

/etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address xx.xx.xx.xx.236
	netmask 255.255.255.248
	network xx.xx.xx.232
	broadcast xx.xx.xx.239
	gateway xx.xx.xx.233
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers xx.xx.xx.2
	dns-search domain.com

auto eth1
iface eth1 inet static
	address 192.168.1.80
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255

```

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:1c:23:ba:5d:1f  
          inet addr:66.185.103.236  Bcast:66.185.103.239  Mask:255.255.255.248
          inet6 addr: fe80::21c:23ff:feba:5d1f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:647964 errors:0 dropped:0 overruns:0 frame:0
          TX packets:751313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:163147260 (163.1 MB)  TX bytes:529973953 (529.9 MB)
          Interrupt:16 Memory:f8000000-f8012700 

eth1      Link encap:Ethernet  HWaddr 00:1c:23:ba:5d:21  
          inet addr:192.168.1.80  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:feba:5d21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2834033 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2532159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1199739637 (1.1 GB)  TX bytes:634079741 (634.0 MB)
          Interrupt:16 Memory:f4000000-f4012700 

```

route -ve
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
localnet        *               255.255.255.248 U         0 0          0 eth0
192.168.1.0     *               255.255.255.0   U         0 0          0 eth1
default         xx.xx.xx.233  0.0.0.0         UG        0 0          0 eth0

```

---

### Post by Iowan on 2009-01-07
Almost sounds like you have a power saving option kicking in.  (acpi, BIOS?)

---

### Post by Jayock on 2009-01-08
Definately not in bios.  Why would one port always function while the other is not?  They are both on the same integrated lan card.  

Where can I check ACPI for Ubuntu?

---

### Post by Jayock on 2009-01-08
Definately not in bios.  Why would one port always function while the other is not?  They are both on the same integrated lan card.  

Where can I check ACPI for Ubuntu?

---

