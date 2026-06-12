---
title: "wired connection does not work"
date: 2013-04-10
forum: Networking &amp; Wireless
---

### Post by perro68 on 2013-04-10
I have a dual boot machine....When i boot into windows my network works fine both wireless and wired connection

when i boot into ubuntu i can only connect wirelessly i would like to use my router via the ehternet cable

I have no idea how do diagnose the proble much less solve it  i know that the machine sees the connection at eth0

when i go into the network settings a wired connection is listed ...but it is never able to connect

please help

some how i know it is something simple if i had more knowledge of ubuntu

i am using 12.10

---

### Post by papibe on 2013-04-10
Hi perro68.

Could you post the results of these commands while trying to connect using your wired connection?
```
sudo lshw -C network

lspci -nnk | grep -iA3 eth

ifconfig

route -n

nslookup ubuntu.com

dig ubuntuforums.org
```
Regards.

---

### Post by perro68 on 2013-04-11
Thank you in advance for u help ...i do hope u will still help ....I will post when i get home ....I did not see your reply until after i got to work

---

### Post by perro68 on 2013-04-11
Ok this is what i get when trying to use my lan (wired) connection only
the wireless connection works fine ..this is with wireess disconnected and trying to connect via the wired connection

i hope u can help

sudo lshw -C network

```
*-network               
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 08
       serial: 78:e3:b5:b2:81:3b
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx driverversion=1.2.3 duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:19 memory:fea00000-fea3ffff ioport:e000(size=128)
  *-network
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 68:94:23:39:1a:9f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.5.0-27-generic firmware=0.34 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:fe900000-fe90ffff
```

---

### Post by perro68 on 2013-04-11
lspci -nnk | grep -iA3 eth
```
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 08)
    Subsystem: Hewlett-Packard Company Device [103c:2ae0]
    Kernel driver in use: alx
    Kernel modules: alx

```



ifconfig


```
eth0      Link encap:Ethernet  HWaddr 78:e3:b5:b2:81:3b  
          inet6 addr: fe80::7ae3:b5ff:feb2:813b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2360 (2.3 KB)  TX bytes:15130 (15.1 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14654 (14.6 KB)  TX bytes:14654 (14.6 KB)

wlan0     Link encap:Ethernet  HWaddr 68:94:23:39:1a:9f  
          inet6 addr: fe80::6a94:23ff:fe39:1a9f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3550498 (3.5 MB)  TX bytes:389172 (389.1 KB)




```


route -n

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```


nslookup ubuntu.com

```
;; connection timed out; no servers could be reached
```







dig ubuntuforums.org
```
; <<>> DiG 9.8.1-P1 <<>> ubuntuforums.org
;; global options: +cmd
;; connection timed out; no servers could be reached
```

---

### Post by Iowan on 2013-04-11
No routing info - probably a bad thing...
Does it have info when wireless?

---

### Post by perro68 on 2013-04-11
> **Iowan said:**
> No routing info - probably a bad thing...
Does it have info when wireless?


yes it does

route -n gives

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
```

---

### Post by perro68 on 2013-04-11
> **Iowan said:**
> No routing info - probably a bad thing...
Does it have info when wireless?

ifconfig gives
```

eth0      Link encap:Ethernet  HWaddr 78:e3:b5:b2:81:3b  
          inet6 addr: fe80::7ae3:b5ff:feb2:813b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:9808 (9.8 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12288 (12.2 KB)  TX bytes:12288 (12.2 KB)

wlan0     Link encap:Ethernet  HWaddr 68:94:23:39:1a:9f  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6a94:23ff:fe39:1a9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1392 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1383434 (1.3 MB)  TX bytes:189960 (189.9 KB)
```

---

### Post by Iowan on 2013-04-11
Sorry - my bad...
What are results of **route -n** when wireless is active (working)?

---

### Post by perro68 on 2013-04-11
when wireless is active i get this

yes it does

route -n gives

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
```

---

### Post by Iowan on 2013-04-11
I haven't gotten comfortable w/ IPv6, but I notice wireless uses IPv4 addresses, and eth0 has no IPv4 address. You might check Network Manager settings for IPv4 on eth0...

---

### Post by perro68 on 2013-04-11
> **Iowan said:**
> I haven't gotten comfortable w/ IPv6, but I notice wireless uses IPv4 addresses, and eth0 has no IPv4 address. You might check Network Manager settings for IPv4 on eth0...

exactly what am i checking ....it is set for auto dhcp

---

### Post by Iowan on 2013-04-11
Is it set to "Connect Automatically" and "Available to all users"? 
Curiously, this machine calls the connection "Auto Ethernet" instead of "Auto eth0"...

---

### Post by perro68 on 2013-04-11
IT seems to be a case of the driver for my etheri think i solved it my is seemed to be dealing with the driver

```
apt-cache search linux-backports-modules
sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
sudo modprobe alx
```



after rebooting the connection came right up 
net cart

---

