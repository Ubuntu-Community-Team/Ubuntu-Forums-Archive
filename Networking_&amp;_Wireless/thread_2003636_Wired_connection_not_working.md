---
title: "Wired connection not working"
date: 2012-06-14
forum: Networking &amp; Wireless
---

### Post by sharkswlasers on 2012-06-14
I'm terribly sorry for troubling anyone, but as I've spent the last day and a half scouring these forums and other corners of the internet for a solution, I at least feel as though I've put in my due diligence before posting.

Symptoms:

- wired connection is not working on ubuntu 12.04. Also does not work when booting from a live 12.04 cd. Wired card DOES work when booting to windows xp (dual boot laptop). This problem is a relatively recent onset, early this week.

- When only a wired connection is allowed, the machine hangs on "looking up www.website.com", and ping [www.website.com]("http://www.website.com") hangs as well. This initially led me to believe that i had a DNS lookup issue, and I went through pains to figure out how to get that properly added to resolv.conf, however, this did not fix the problem. Furthermore, the live CD would definitely not have DNS lookup issues (at least, i think), so I think i'm on reasonable ground to say its not dns.

- wireless connection is fine. Machine is a Dell Latitude E6400 which does need a special wireless driver, but i've been dealing with this for years and it hasn't been an issue.

Contents of /etc/resolv.conf:
```
nameserver 127.0.0.1
search its.yale.edu
```Contents of /etc/network/interfaces:
```
auto lo
iface lo inet loopback
```While doing my reading, this struck me as an odd interfaces file, as there isnt a pair of lines: auto eth0, iface eth0 inet dhcp. However, if I add these lines the wired card is just unable to connect and network manager gets angry. These files were identical when booting from the Live CD.

To check the DNS, i added dns-search and dns-nameservers lines to the interfaces file, and upon rebooting, these were appropriately added to resolv.conf. However, this did not fix the problem.

running route -n:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         128.36.14.1     0.0.0.0         UG    0      0        0 eth0
10.160.32.0     0.0.0.0         255.255.224.0   U     2      0        0 eth1
128.36.14.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

```

running ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:24:e8:ba:68:6d  
          inet addr:128.36.14.101  Bcast:128.36.14.255  Mask:255.255.255.0
          inet6 addr: 2604:b200:4:527:224:e8ff:feba:686d/64 Scope:Global
          inet6 addr: fe80::224:e8ff:feba:686d/64 Scope:Link
          inet6 addr: 2604:b200:4:527:8e6:a067:d0e7:bc69/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27103 errors:0 dropped:8 overruns:0 frame:0
          TX packets:2951 errors:13 dropped:0 overruns:0 carrier:13
          collisions:214 txqueuelen:1000 
          RX bytes:4612104 (4.6 MB)  TX bytes:563554 (563.5 KB)
          Interrupt:22 Memory:f6ae0000-f6b00000 

eth1      Link encap:Ethernet  HWaddr 00:26:5e:25:80:70  
          inet addr:10.160.63.146  Bcast:10.160.63.255  Mask:255.255.224.0
          inet6 addr: fe80::226:5eff:fe25:8070/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:280819 errors:0 dropped:0 overruns:0 frame:137311
          TX packets:50908 errors:109 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:94583953 (94.5 MB)  TX bytes:5652119 (5.6 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:344911 (344.9 KB)  TX bytes:344911 (344.9 KB)

```running lshw -C network
```
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:ba:68:6d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=half firmware=1.7-7 ip=128.36.14.101 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f6ae0000-f6afffff memory:f6adb000-f6adbfff ioport:efe0(size=32)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:26:5e:25:80:70
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=10.160.63.146 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff

```Thanks a bunch in advance. Please let me know if there are any other diagnostic tools that you would like to run for more information.

---

### Post by brent1975 on 2012-06-14
> **sharkswlasers said:**
> I'm terribly sorry for troubling anyone, but as I've spent the last day and a half scouring these forums and other corners of the internet for a solution, I at least feel as though I've put in my due diligence before posting.

Symptoms:

- wired connection is not working on ubuntu 12.04. Also does not work when booting from a live 12.04 cd. Wired card DOES work when booting to windows xp (dual boot laptop). This problem is a relatively recent onset, early this week.

- When only a wired connection is allowed, the machine hangs on "looking up www.website.com", and ping [www.website.com]("http://www.website.com") hangs as well. This initially led me to believe that i had a DNS lookup issue, and I went through pains to figure out how to get that properly added to resolv.conf, however, this did not fix the problem. Furthermore, the live CD would definitely not have DNS lookup issues (at least, i think), so I think i'm on reasonable ground to say its not dns.

- wireless connection is fine. Machine is a Dell Latitude E6400 which does need a special wireless driver, but i've been dealing with this for years and it hasn't been an issue.

Contents of /etc/resolv.conf:
```
nameserver 127.0.0.1
search its.yale.edu
```Contents of /etc/network/interfaces:
```
auto lo
iface lo inet loopback
```While doing my reading, this struck me as an odd interfaces file, as there isnt a pair of lines: auto eth0, iface eth0 inet dhcp. However, if I add these lines the wired card is just unable to connect and network manager gets angry. These files were identical when booting from the Live CD.

To check the DNS, i added dns-search and dns-nameservers lines to the interfaces file, and upon rebooting, these were appropriately added to resolv.conf. However, this did not fix the problem.

running route -n:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         128.36.14.1     0.0.0.0         UG    0      0        0 eth0
10.160.32.0     0.0.0.0         255.255.224.0   U     2      0        0 eth1
128.36.14.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

```running ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:24:e8:ba:68:6d  
          inet addr:128.36.14.101  Bcast:128.36.14.255  Mask:255.255.255.0
          inet6 addr: 2604:b200:4:527:224:e8ff:feba:686d/64 Scope:Global
          inet6 addr: fe80::224:e8ff:feba:686d/64 Scope:Link
          inet6 addr: 2604:b200:4:527:8e6:a067:d0e7:bc69/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27103 errors:0 dropped:8 overruns:0 frame:0
          TX packets:2951 errors:13 dropped:0 overruns:0 carrier:13
          collisions:214 txqueuelen:1000 
          RX bytes:4612104 (4.6 MB)  TX bytes:563554 (563.5 KB)
          Interrupt:22 Memory:f6ae0000-f6b00000 

eth1      Link encap:Ethernet  HWaddr 00:26:5e:25:80:70  
          inet addr:10.160.63.146  Bcast:10.160.63.255  Mask:255.255.224.0
          inet6 addr: fe80::226:5eff:fe25:8070/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:280819 errors:0 dropped:0 overruns:0 frame:137311
          TX packets:50908 errors:109 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:94583953 (94.5 MB)  TX bytes:5652119 (5.6 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:344911 (344.9 KB)  TX bytes:344911 (344.9 KB)

```running lshw -C network
```
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:ba:68:6d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=half firmware=1.7-7 ip=128.36.14.101 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f6ae0000-f6afffff memory:f6adb000-f6adbfff ioport:efe0(size=32)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:26:5e:25:80:70
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=10.160.63.146 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff

```Thanks a bunch in advance. Please let me know if there are any other diagnostic tools that you would like to run for more information.

I came from 10.04 to 12.04 and came across this issue. From what I read and is working for me is instead of putting the name servers in /etc/resolv.cof place them at the bottom of /etc/network/interfaces
Here is what mine looks like... Take in mine this is just a home server

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static

        address 192.168.2.106
        netmask 255.255.255.0
        network 192.168.2.0
        gateway 192.168.2.1
        broadcast 192.168.2.255

        dns-nameservers 8.8.8.8
        dns-search google.com

---

### Post by sharkswlasers on 2012-06-14
i work in an office and i think i need to maintain dhcp. but adding:

auto eth0
iface eth0 inet dhcp

causes my wired connection to just stop working

---

