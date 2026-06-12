---
title: "Wireless only works when laptop plugged in?  Broadcom/10.10/HP dv9000"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by brianbob on 2010-10-22
HP Pavilion dv9000
Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller
Ubuntu 10.10 64-bit

If I boot into ubuntu with my laptop plugged in, the wireless works fine. However, if I boot without plugging in my laptop, or the laptop sleeps and wakes up without the power cord plugged in,  network manager and wcid show no available networks. I tried 
```

sudo /etc/init.d/networking restart

```
to no avail. I don't know if this is some weird power management thing or what.

```

sudo lshw -C network
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:a2:f8:e2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=10.33.4.167 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:42 memory:f6488000-f6488fff ioport:30f8(size=8) memory:f6489c00-f6489cff memory:f6489800-f648980f
  *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:36:9d:60
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:19 memory:f6000000-f6003fff

```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

---

### Post by Iowan on 2010-10-22
That DOES sound like a power management-related problem. This Jaunty laptop has an option under Preferences>Power Management. The BIOS might also have some settings.

---

### Post by brianbob on 2010-10-24
Do you know where would I find these settings? The power management menu in the System->Preferences only deals with the backlight, hibernation and the like. The BIOS didn't have a power management option in the setup setup menu either.

Would there be some system or configuration file somewhere that deals with this?

---

### Post by brianbob on 2010-10-24
I've tried
```
sudo iwconfig eth1 power off
```

and adding "wireless-power off" to /etc/network/interfaces with no luck.

Any ideas?

---

### Post by brianbob on 2010-11-05
Here the output when the laptop is plugged in and working:
```

brian@brian-HP-Pavilion-dv9700:~$ sudo ifup eth1
ifup: interface eth1 already configured

```

```

brian@brian-HP-Pavilion-dv9700:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:212  Noise level:165
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


```

```
 
brian@brian-HP-Pavilion-dv9700:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:a2:f8:e2  
          inet addr:10.33.4.167  Bcast:10.33.4.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fea2:f8e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:373 errors:0 dropped:0 overruns:0 frame:0
          TX packets:283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:193040 (193.0 KB)  TX bytes:34993 (34.9 KB)
          Interrupt:11 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:36:9d:60  
          inet addr:172.25.33.100  Bcast:172.25.33.255  Mask:255.255.254.0
          inet6 addr: fe80::221:ff:fe36:9d60/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:117116
          TX packets:24 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6777 (6.7 KB)  TX bytes:4625 (4.6 KB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

```

```
 
brian@brian-HP-Pavilion-dv9700:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:a2:f8:e2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=10.33.4.167 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:11 memory:f6488000-f6488fff ioport:30f8(size=8) memory:f6489c00-f6489cff memory:f6489800-f648980f
  *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:36:9d:60
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=172.25.33.100 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:10 memory:f6000000-f6003fff

```

```
 
brian@brian-HP-Pavilion-dv9700:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

```

and here is the output when the laptop is running on battery:
```

brian@brian-HP-Pavilion-dv9700:~$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.

```

```

brian@brian-HP-Pavilion-dv9700:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:221
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

```

brian@brian-HP-Pavilion-dv9700:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:a2:f8:e2  
          inet addr:10.33.4.167  Bcast:10.33.4.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fea2:f8e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51661 (51.6 KB)  TX bytes:19014 (19.0 KB)
          Interrupt:11 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:36:9d:60  
          inet6 addr: fe80::221:ff:fe36:9d60/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

```

```

brian@brian-HP-Pavilion-dv9700:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:a2:f8:e2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=10.33.4.167 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:11 memory:f6488000-f6488fff ioport:30f8(size=8) memory:f6489c00-f6489cff memory:f6489800-f648980f
  *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:36:9d:60
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:10 memory:f6000000-f6003fff

```

```

brian@brian-HP-Pavilion-dv9700:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

```

So when the laptop isn't plugged in, my wireless card (eth1) is an unknown interface, but when the laptop is plugged in the card works fine? What would cause that?

Also, shouldn't my wireless card have something from "iwlist scanning"? It worries me that plugged in or not there is nothing there...

---

