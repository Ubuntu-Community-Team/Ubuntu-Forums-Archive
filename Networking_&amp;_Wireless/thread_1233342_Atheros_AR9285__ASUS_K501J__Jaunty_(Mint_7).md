---
title: "Atheros AR9285 | ASUS K501J | Jaunty (Mint 7)"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by Giovanni Gale on 2009-08-06
I pretty much cannot get the internal wireless in my laptop to do anything whatsoever under Linux Mint 7 (based on Jaunty). It works perfectly on my Windows partition, so the hardware isn't the problem. I also have the problem that my wireless devices on/off button (Fn+F2) does nothing either (have seen this problem with a lot of different ASUS laptops while searching the webs). I can see my wireless device and all its information in the Device Manager app I downloaded from Synaptic, so it is being detected by the system.

Please be specific with any steps you give me to try fixes, since I'm not fully accustomed to everything in this distro yet.

My wireless cards output for lspci is:
```
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:26:18:22:bd:20  
          inet6 addr: fe80::226:18ff:fe22:bd20/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:139 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:18551 (18.5 KB)  TX bytes:16172 (16.1 KB)
          Interrupt:248 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2784 (2.7 KB)  TX bytes:2784 (2.7 KB)
```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

lshw:
```
*-network UNCLAIMED     
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: b0
       serial: 00:26:18:22:bd:20
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no module=atl1e multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8e:8a:51:d8:7c:0e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by moore.bryan on 2009-08-06
[this thread]("http://ubuntuforums.org/showthread.php?t=1230823") seemed to work for some...

---

### Post by Giovanni Gale on 2009-08-06
I got wireless working with the suggestion here:
[http://ubuntuforums.org/showpost.php?p=7744131&postcount=4]("http://ubuntuforums.org/showpost.php?p=7744131&postcount=4")

The Fn+F2 hotkey still does nothing though. =\

---

### Post by moore.bryan on 2009-08-08
Good to hear! Happy Ubuntu-ing.

---

