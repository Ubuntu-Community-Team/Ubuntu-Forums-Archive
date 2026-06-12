---
title: "2 nic's - 2 seperate networks..."
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by Plasma_NZ on 2011-07-29
Ok heres the gist...

have 2 nics, currently only enabling one so this pc has internet....
 
disabled the second cause no-matter the sett's i set it seems to mess up eth0

This is my goal..

eth0 - internet
eth1 - wireless ap - which i only want to be able to access samba-shares

current ifconfig is as follows

```

eth0      Link encap:Ethernet  HWaddr 00:1a:4d:9e:c7:65  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe9e:c765/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10852 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8423826 (8.4 MB)  TX bytes:1680775 (1.6 MB)
          Interrupt:41 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:25:86:e0:00:ee  
          inet addr:192.167.0.1  Bcast:192.167.255.255  Mask:255.255.0.0
          inet6 addr: fe80::225:86ff:fee0:ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3802 (3.8 KB)  TX bytes:62664 (62.6 KB)
          Interrupt:16 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2940 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:189001 (189.0 KB)  TX bytes:189001 (189.0 KB)

```

How so i resolve this so when i enabled eth1 it doesnt cause eth0 to go blind to the internet..?

---

### Post by karlson on 2011-07-29
> **Plasma_NZ said:**
> Ok heres the gist...

have 2 nics, currently only enabling one so this pc has internet....
 
disabled the second cause no-matter the sett's i set it seems to mess up eth0

This is my goal..

eth0 - internet
eth1 - wireless ap - which i only want to be able to access samba-shares

current ifconfig is as follows

```

eth0      Link encap:Ethernet  HWaddr 00:1a:4d:9e:c7:65  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe9e:c765/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10852 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8423826 (8.4 MB)  TX bytes:1680775 (1.6 MB)
          Interrupt:41 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:25:86:e0:00:ee  
          inet addr:192.167.0.1  Bcast:192.167.255.255  Mask:255.255.0.0
          inet6 addr: fe80::225:86ff:fee0:ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3802 (3.8 KB)  TX bytes:62664 (62.6 KB)
          Interrupt:16 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2940 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:189001 (189.0 KB)  TX bytes:189001 (189.0 KB)

```

How so i resolve this so when i enabled eth1 it doesnt cause eth0 to go blind to the internet..?

Correct mask on eth1 interface would be a good start.  Also what does ```
netstat -rn
``` show?

---

### Post by Plasma_NZ on 2011-07-29
```

eth0      Link encap:Ethernet  HWaddr 00:1a:4d:9e:c7:65  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe9e:c765/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15589 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15071 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11447669 (11.4 MB)  TX bytes:2278830 (2.2 MB)
          Interrupt:41 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:25:86:e0:00:ee  
          inet addr:192.167.0.1  Bcast:192.167.0.255  Mask:255.255.255.0
          inet6 addr: fe80::225:86ff:fee0:ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:885 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5452 (5.4 KB)  TX bytes:90557 (90.5 KB)
          Interrupt:16 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3941 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3941 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:251528 (251.5 KB)  TX bytes:251528 (251.5 KB)

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.167.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0

```

---

### Post by karlson on 2011-07-29
> **Plasma_NZ said:**
> ```


Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.167.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0

```

Is you eth1 interface facing the internet?  If not set the address to 192.168.1.x instead of 192.167.0.x.

---

### Post by Plasma_NZ on 2011-07-29
eth0 = internet
eth1 = wireless ap - which i dont want to access anything but samba shares

---

### Post by karlson on 2011-07-29
> **Plasma_NZ said:**
> eth0 = internet
eth1 = wireless ap - which i dont want to access anything but samba shares

Then change the IP address to be on 192.168.1.x subnet.

---

### Post by Plasma_NZ on 2011-07-29
i cannot use 192.168.1.* range as thats in use on 192.168.0.1 routing server

---

### Post by karlson on 2011-07-30
> **Plasma_NZ said:**
> i cannot use 192.168.1.* range as thats in use on 192.168.0.1 routing server

If your mask is set as it is now to class C(255.255.255.0, the range 192.168.0.x doesn't include 192.168.1.x

---

### Post by Plasma_NZ on 2011-07-30
despite what you are saying - if i type in my browser 192.168.1.2 - i end up accessing my router...

---

### Post by karlson on 2011-07-30
> **Plasma_NZ said:**
> despite what you are saying - if i type in my browser 192.168.1.2 - i end up accessing my router...

Do you have a machine that has IP address of 192.168.1.2?  Secondly how is your router configured? and what kind of router is it?

---

### Post by Plasma_NZ on 2011-07-30
solved..

---

