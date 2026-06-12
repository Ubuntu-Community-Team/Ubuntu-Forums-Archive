---
title: "No wired LAN on acer revo"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by retrodans on 2011-05-22
I recently got an acer revo, and followed various tutorials on getting it setup, and largely it appears to be working now.

That is, except for the wired LAN (wireless is fine).  It says it has connected to auto eth, but whenever i try to access any network/online resource, I get nothing:

```
ping www.google.com
```
returns: unknown host

When I run the route command, I see 2 rows (link-local and 224.0.0.0) should there be one for 192.168.0.1 (my router)?  When I have wireless on, the row appears.

Sorry for the vagueness of my help request, if you have any advice, or want more information, let me know.

Thanks,
Dan

---

### Post by Iowan on 2011-05-22
Post the results of **route -n**. 
**ifconfig -a** shows the interface with an IP address?
Is that a DHCP address?

---

### Post by retrodans on 2011-05-22
the below results are with wireless disabled

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1      0        0 eth0
224.0.0.0       0.0.0.0         240.0.0.0       U     0      0        0 eth0

```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr d0:27:88:22:fd:e1  
          inet addr:169.254.10.247  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::d227:88ff:fe22:fde1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9697 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:775898 (775.8 KB)  TX bytes:495457 (495.4 KB)
          Interrupt:43 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8225 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:878335 (878.3 KB)  TX bytes:878335 (878.3 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:a4:60:27  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:68805 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17989284 (17.9 MB)  TX bytes:1960228 (1.9 MB)
          Interrupt:18 

```

as for dhcp, it was fixed ip, but i recently turned it of for this machine in case it was causing the issue. so currently ip is set dynamically bt router

---

### Post by Iowan on 2011-05-22
The 169.254.X.X address suggests the machine failed to get an IP address from the router/DHCP Server and **avahi** stepped in to provide one. (Unfortunately, that probably puts the machine in a network by itself). The 240.X.X.X is a new one for me...

**sudo dhclient eth0** will *probably* show no address offers received.

---

### Post by retrodans on 2011-05-22
Running the command:
```
sudo dhclient eth0
```
Disconnected the ethernet but did not reconnect again (although it appeared to try).  No messages were returned in terminal to give me a feel as to why.  Also, my ethernet doesn't even pretend to connect anymore.

---

### Post by Iowan on 2011-05-22
Curious - ordinarily that unsuccessful command would yield something like:
```
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Does **sudo lshw -C network** reveal anything interesting?
This is the 8.10 box? (Seems like 11.04 had some driver issues earlier)

---

### Post by retrodans on 2011-05-22
Sorry no, I will run that command in a moment, but the v.8 was for my other computer.  The revo is running the newest version of Ubuntu (11.04).  Sorry if this has caused any wasted time.

What were the driver issues which were there?  The tutorial I used for setup may have skirted around one of those, just wondering whether the fix was to get WiFi working at the expense of eth.

Will get the results of the command below soon.

---

### Post by retrodans on 2011-05-22
result of sudo lshw -C network

```
  *-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 1c:65:9d:a4:60:27
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:18 memory:febf0000-febfffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: d0:27:88:22:fd:e1
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:e800(size=256) memory:fbffb000-fbffbfff memory:fbffc000-fbffffff

```

---

### Post by retrodans on 2011-05-27
Not sure where I can go with the information at moment, anyone able to advise?  I would rather not do a complete reinstall if I could help it (in fact, I probably wont do it if that's the only option) just because I have it mostly setup in my own fashion.

Thanks for your advise,
Dan

---

### Post by retrodans on 2011-10-16
Ok, just upgraded to 11.10 and realised the problem returned, I returned to my post to realise that on this occassion I hadn't put in my solution.  So here it is.  I went into my network settings, and saw that the ip was set to 'link-local', I am not sure what that is, but setting to DHCP solved the issue, and no I have internet again.

Hope this helps someone.

---

