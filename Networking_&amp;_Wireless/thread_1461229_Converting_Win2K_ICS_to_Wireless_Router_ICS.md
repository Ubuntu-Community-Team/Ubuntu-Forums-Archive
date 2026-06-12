---
title: "Converting Win2K ICS to Wireless Router ICS"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by Robynsveil on 2010-04-23
I've had a Windows2000-based ICS network for years. The Linux boxes could see the Windows boxes and read and write to them. Everyone had access to the Internet. The layout was basically this:

Internet -> Cable Modem -> Win2K box with ICS -> smart switch -> all clients

We recently replaced the ageing Win2K box with a SMC Barricade N Wireless 4 port broadband router. So now we have wireless access to Internet as well as wired (for the desktops without wireless devices):

Internet -> Cable Modem -> Wireless Router -> smart switch -> wired clients
...........................................-> wireless clients

All boxes can see the Internet. All Windows boxes can see each other. None of the Linux boxes can see any of the home network. When I click on Network in the Places area of the File Browser, I can see the Windows Network Icon, and double-click on that gives me the Icon for the Home Network by name, but double-clicking on that brings up a long wait and finally the message:
"Unable to mount location - Failed to retrieve share list from server"

Is there any other information I need to provide to trouble-shoot this issue?

---

### Post by Robynsveil on 2010-04-24
Okay, reading on this forum has got me asking the network a few questions:

```
ifconfig -a
```

gets me:

> eth0      Link encap:Ethernet  HWaddr 00:24:8c:11:b3:6d  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:8cff:fe11:b36d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86867 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30660 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23820646 (23.8 MB)  TX bytes:5099489 (5.0 MB)
          Interrupt:252 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6128 (6.1 KB)  TX bytes:6128 (6.1 KB)

pan0      Link encap:Ethernet  HWaddr 3a:cb:c0:c6:f3:d6  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:e0:dd:9e  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-E0-DD-9E-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

... and ...
```
sudo lshw -C network
```
gets me:

> *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:24:8c:11:b3:6d
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.102 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:af:e0:dd:9e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3a:cb:c0:c6:f3:d6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


Thanks in advance for any ideas you can give. I did try inserting this:

```
send vendor-class-identifier "MSFT 5.0";
```

into the /etc/dhcp3/dhclient.conf file but no joy... not really sure where to look next.

---

### Post by Robynsveil on 2010-04-24
I'm going to try to be resplendent with salient information:

```
ifconfig
```

gives me:

> 
eth0      Link encap:Ethernet  HWaddr 00:24:8c:11:b3:6d  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:8cff:fe11:b36d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:90526 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25719604 (25.7 MB)  TX bytes:5324265 (5.3 MB)
          Interrupt:252 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6128 (6.1 KB)  TX bytes:6128 (6.1 KB)


... and ... ```
route -n
``` gets me:
> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0


---

### Post by Robynsveil on 2010-04-24
Oh, and this:

```
sudo smbtree
```
got me:

> 
DANCERS
	\\FLIGHT         		Flight
timeout connecting to 199.101.28.130:445
timeout connecting to 199.101.28.130:139
cli_start_connection: failed to connect to FLIGHT<20> (0.0.0.0). 
Error NT_STATUS_ACCESS_DENIED

where "DANCERS" is the name of the workgroup and "Flight" is a WinXP Pro box with shares on it... there are other WinXP and Ubuntu boxes with shares on this network, but this is the only one that shows. findsmb got me nothing:

>                          *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------


---

### Post by Robynsveil on 2010-04-24
To those of you 57 lurkers who are wondering how this issue was solved, I refer you to this page:
[http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")

I only needed to go as far as the:

```
sudo apt-get install winbind
```

and voila, there was my Windows share, back again! Yay!!!

---

