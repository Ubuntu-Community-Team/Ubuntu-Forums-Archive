---
title: "help ading a third nic"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by lihnuz on 2010-11-29
Hello. im having som trubbel adding a third nic to my ubuntu-server (its being used as a router)

what i have is:
eth0 (connected to internet)
eth1 (connected to desktop)

what i want to add:
eth2 (connected to a wierles router)

At the moment i have eth0 and eth1 working, and i want to add a third network card, so that devices connected to that can connect to the internet and my local network

Right now I have eth2 working as far as it starts up, and the connected router gets an ip, but devices connected to the wierles router cant connect to the internet, and my desktop cant connect to the router (to access the admin interface on the 
router)

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:19:db:20:c2:78
          inet addr:xxx.xxx.xxx.xxx  Bcast:xxx.xxx.xxx.xxx  Mask:255.255.255.128
          inet6 addr: fe80::219:dbff:fe20:c278/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3884 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1869228 (1.8 MB)  TX bytes:512122 (512.1 KB)
          Interrupt:23 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:1b:21:25:40:45
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:21ff:fe25:4045/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2055 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3465 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:549998 (549.9 KB)  TX bytes:1814080 (1.8 MB)

eth2      Link encap:Ethernet  HWaddr 00:11:95:80:88:3e
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1008 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:129779 (129.7 KB)  TX bytes:129779 (129.7 KB)

```

 cat /etc/network/interfaces
```

# The loopback network interface
auto lo eth0 eth1 eth2
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet static
        address 192.168.0.1
        netmask 255.255.255.0
        network 192.168.0.0

iface eth2 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        network 192.168.0.0


```

anyone have any suggestions on what i should do?

---

### Post by Iowan on 2010-11-29
```
iface eth2 inet static
        address 192.168.[COLOR="Red"]1[/COLOR].1
        netmask 255.255.255.0
        network 192.168.[COLOR="Red"]0.[/COLOR]0
```
This probably isn't gonna work...

---

### Post by lihnuz on 2010-11-30
You are right about that, changed that so the ../interfaces file looks likes folows for eth2

```

iface eth2 inet static
        address 192.168.0.10
        netmask 255.255.255.0
        network 192.168.0.0

```

And after that when i plug in a network device in that nic I get a dhcp respones and a ip is handed out to that device. But, i still cant get it to work. When i try to connect to the server via ssh i get "connection lost, no route to host"

```

lihnuz@stol > route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.xxx.100.128  *               255.255.255.128 U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth2
default         xxx-xx-100-129. 0.0.0.0         UG    100    0        0 eth0


```

Don't know if this might help, but im guessing the problem is to find here somewhere?

---

### Post by lihnuz on 2010-11-30
Ive gotten a bit further now, figured out that i had to have the tow nics on different subnets, and that handling both nic:s whit a dhcp-conf that was setup to work with only one nic might not been the smartest idea

What i need help whit now is, ether, help to conf dhcp handing out different ip-subnets (192.168.0.* to eth1 and 192.168.1.* to eth2) or (and i thought this would be easy but i have come up whit nothing usfull) conf the server so that i can configure the network device i put on eth2 to use static ip

Anny pointers to do ether of those would be very appreciated

---

### Post by Iowan on 2010-12-01
One possible solution would be to configure your DHCP server to assign a static lease based on MAC address... assuming the DHCP server is a different machine. Servers usually have fixed addresses for their NIC's anyway.

I'm probably misunderstanding your goals - sounds like the server IS the DHCP server, and you want to hand out different IP addresses based on which interface the request comes through.

---

