---
title: "Configuration problem of two NIC"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by freeburn on 2009-12-13
I have two NIC. one is connected to a private network. and ip of that network is determined by dhcp. 

another NIC is connected to another network. for that network, ip is specifically assigned by the network administrator of that network.  

eth0 is connected to that dedicated line and eth1 is connected to my office network. 

i'm giving the configuration of the two network.

```

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:1D:7E:5E:4D  
          inet addr:192.168.250.186  Bcast:192.168.250.191  Mask:255.255.255.248
          inet6 addr: fe80::224:1dff:fe7e:5e4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:3651666419 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:640 (640.0 b)  TX bytes:12065 (11.7 KiB)
          Interrupt:16 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:21:27:FC:60:BB  
          inet addr:192.168.12.11  Bcast:192.168.12.255  Mask:255.255.255.0
          inet6 addr: fe80::221:27ff:fefc:60bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 

route -n

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.250.184 0.0.0.0         255.255.255.248 U     0      0        0 eth0
192.168.12.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth1
0.0.0.0         192.168.12.1    0.0.0.0         UG    0      0        0 eth1


```


problem is i'm connected to the office network without any problem but i can't telnet to the other line. if i turn off the other network then i can telnet the dedicated line.

plz help me with this.

---

### Post by Iowan on 2009-12-13
To this untrained eye, the setup looks proper (except the RX packets dropped count). Dunno what the 192.168.122.0 on virbr0 is doing. 
Does the machine happen to have a firewall running?

---

