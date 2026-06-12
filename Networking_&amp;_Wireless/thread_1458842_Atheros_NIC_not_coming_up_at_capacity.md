---
title: "Atheros NIC not coming up at capacity"
date: 2010-04-20
forum: Networking &amp; Wireless
---

### Post by t-readyroc on 2010-04-20
Just rebuilt my file/print server using an ECS 945GCD-M Atom motherboard.  Running it under 9.10 (2.6.31-20) using the same cable and port on my Netgear switch that my old server connected to at 1GB/s without issue (old server's NIC was Intel-based).

Did some forum searching.  Found the driver is an AR813x, & downloaded & installed the latest driver from [here]("http://partner.atheros.com/Drivers.aspx") (1.0.1.9).   sudo lshw -C network now shows that it's using the new driver, but still sitting at 100MB/s:

```
  *-network               
       description: Ethernet interface
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 00:25:11:c4:fa:d4
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1C driverversion=1.0.1.9 duplex=full firmware=L1e ip=192.168.0.2 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:25 memory:febc0000-febfffff ioport:ec00(size=128)

```/etc/init.d/networking restart does the following:
```
 * Reconfiguring network interfaces...
Ignoring unknown interface eth0=eth0.
   ...done.

```ifconfig output:
```
eth0      Link encap:Ethernet  HWaddr 00:25:11:c4:fa:d4  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::225:11ff:fec4:fad4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:182 errors:0 dropped:0 overruns:0 carrier:10
          collisions:0 txqueuelen:1000 
          RX bytes:21670 (21.6 KB)  TX bytes:23807 (23.8 KB)
          Interrupt:25 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:189 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20934 (20.9 KB)  TX bytes:20934 (20.9 KB)
```/etc/network/interfaces :
```
auto lo
iface lo inet loopback

```I can't seem to get it to come up at the full 1GB/s.  I also tried ethtool -s eth0 speed 1000 without success.  Also, any idea why networking restart ignores eth0?  Any help would be appreciated.

---

### Post by t-readyroc on 2010-04-20
It was the dang Netgear (GS605).  I unplugged & plugged the dang cable back in & it came up @ 1GB/s just fine :rolleyes:

---

