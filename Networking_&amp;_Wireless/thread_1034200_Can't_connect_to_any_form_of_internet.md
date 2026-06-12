---
title: "Can't connect to any form of internet?"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by epicbattle on 2009-01-08
Alrighty, I just purchased a shiny new HP Pavilion with 4g ram 320gigs 2 dual 2ghz processors...she's very nice. I set myself up with a dual boot being Ubuntu and the devil(vista). After finally getting Ubuntu up and running on the laptop I HAD internet. Then I downloaded the update. Now I can't get any form of internet (wired or wireless). It's very strange. A lot of the tutorials tell you to run certain commands and download certain programs, but I cannot download anything. What information do you guys need to help me up and running? What's the command to find what kind of wireless and ether net card in Ubuntu? I think you will need that. Anyway... this is what I do know:

HP Pavilion
2 2ghz processor
4gig ram
320gig
 running Ubuntu 8.10 (64 bit)

sorry for being a noob...

---

### Post by melojo on 2009-01-08
goto applications>accessories>terminal and post the output of the commands below.

```


lspci
sudo lshw -C network
ifconfig

```

This will give us more info!

---

### Post by epicbattle on 2009-01-08
```

 lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

```
 *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:3d:ce:f7
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.102 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ba:4b:0e:cb:c6:ed
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```


```
eth0      Link encap:Ethernet  HWaddr 00:23:8b:3d:ce:f7  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe3d:cef7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:789 errors:0 dropped:8649549563 overruns:0 frame:0
          TX packets:787 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:801307 (801.3 KB)  TX bytes:138030 (138.0 KB)
          Interrupt:248 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

respectively. Thanks! I got the wired up and running? It just started when I restarted the pc... weird.

---

### Post by melojo on 2009-01-08
Go to the link below.

[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

### Post by superprash2003 on 2009-01-08
post output of ping 74.125.45.100 from the terminal

---

### Post by epicbattle on 2009-01-09
```
ping 74.125.45.100
PING 74.125.45.100 (74.125.45.100) 56(84) bytes of data.
64 bytes from 74.125.45.100: icmp_seq=1 ttl=242 time=64.8 ms
64 bytes from 74.125.45.100: icmp_seq=2 ttl=242 time=71.3 ms
64 bytes from 74.125.45.100: icmp_seq=3 ttl=242 time=83.1 ms
64 bytes from 74.125.45.100: icmp_seq=4 ttl=242 time=56.5 ms
64 bytes from 74.125.45.100: icmp_seq=5 ttl=242 time=53.2 ms
64 bytes from 74.125.45.100: icmp_seq=6 ttl=242 time=62.2 ms
64 bytes from 74.125.45.100: icmp_seq=7 ttl=242 time=63.2 ms
64 bytes from 74.125.45.100: icmp_seq=8 ttl=242 time=72.8 ms
64 bytes from 74.125.45.100: icmp_seq=9 ttl=242 time=51.9 ms
64 bytes from 74.125.45.100: icmp_seq=10 ttl=242 time=53.9 ms
64 bytes from 74.125.45.100: icmp_seq=11 ttl=242 time=57.4 ms
64 bytes from 74.125.45.100: icmp_seq=12 ttl=242 time=53.0 ms
64 bytes from 74.125.45.100: icmp_seq=13 ttl=242 time=53.4 ms
64 bytes from 74.125.45.100: icmp_seq=14 ttl=242 time=50.7 ms
64 bytes from 74.125.45.100: icmp_seq=15 ttl=242 time=71.0 ms
64 bytes from 74.125.45.100: icmp_seq=16 ttl=242 time=53.2 ms
64 bytes from 74.125.45.100: icmp_seq=17 ttl=242 time=50.6 ms
64 bytes from 74.125.45.100: icmp_seq=18 ttl=242 time=62.9 ms
64 bytes from 74.125.45.100: icmp_seq=19 ttl=242 time=51.3 ms
64 bytes from 74.125.45.100: icmp_seq=20 ttl=242 time=59.4 ms
64 bytes from 74.125.45.100: icmp_seq=21 ttl=242 time=63.4 ms
64 bytes from 74.125.45.100: icmp_seq=22 ttl=242 time=66.9 ms
64 bytes from 74.125.45.100: icmp_seq=23 ttl=242 time=63.3 ms
64 bytes from 74.125.45.100: icmp_seq=24 ttl=242 time=58.0 ms
^G64 bytes from 74.125.45.100: icmp_seq=25 ttl=242 time=51.7 ms
64 bytes from 74.125.45.100: icmp_seq=26 ttl=242 time=54.7 ms
64 bytes from 74.125.45.100: icmp_seq=27 ttl=242 time=64.7 ms
^C
--- 74.125.45.100 ping statistics ---
27 packets transmitted, 27 received, 0% packet loss, time 26102ms
rtt min/avg/max/mdev = 50.611/60.005/83.154/8.031 ms

``` is that what you need?

---

### Post by epicbattle on 2009-01-09
Ok, never mind. I figured it all out. The only thing now is the password nagging. I think there is tutorials for that. How do I mark a post as solved?

---

### Post by superprash2003 on 2009-01-09
under Thread Tools.. please mention how you solved it.. was it a DNS issue..

---

### Post by epicbattle on 2009-01-13
Nope ,I never turned on the hardware. So I just went sys/admin/harware drivers and activated it... Sorry for wasting your guys' time. I didn't mean to.

---

