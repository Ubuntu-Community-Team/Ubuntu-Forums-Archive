---
title: "Periodic Network Dropouts"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by clownschoolphd on 2009-05-13
Hi,

I did a fresh reinstall when 9.04 came out.  Since that time, I've been having problems with periodic network dropouts on my Wired connection.  I've searched and found a few related threads that ask for ifconfig, route, and lshw -C network.  The output of those commands is below.

To fix the issue, I click on the Network Manager Icon in the top panel and re-select my static or DHCP connection.  (the drop outs happen with both connections)  This action resets the network and all is back to normal. 

These dropouts occur anywhere from twice an hour to twice a day.  I may not be looking in the right place, but I can't find any info as to what's happening in syslog or dmesg.

I've been hanging on thinking an update will come and that all will be well again.  But I spend a lot of time logged into remote servers.  When the network drops, my connection is reset and any jobs on the remote server are stopped.  Also, I'm sure I'm annoying the heck out of my coworkers with my constantly changing pidgin status ;).  If anyone can lend a hand or point me in the right direction I'd appreciate it.

The following commands were run while the network was not responding.

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:8b:08:d3:7e  
          inet addr:192.168.35.49  Bcast:192.168.35.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:fe08:d37e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2011700 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1164261 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2446651481 (2.4 GB)  TX bytes:502473119 (502.4 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1119153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1119153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66833381 (66.8 MB)  TX bytes:66833381 (66.8 MB)
```

```
route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.35.0    *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.35.1    0.0.0.0         UG    0      0        0 eth0
```

```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:18:8b:08:d3:7e
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5751-v3.44a ip=192.168.35.49 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=1GB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ba:bf:32:17:52:8d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by donato roque on 2009-05-14
This exact same thing is happening to me except it happens more frequently and it happens when i Have my torrent client open and I am downloading torrents.  My thought is it's traffic choking on the downloads or something more sinister like ISP's throttling bandwidth.  It doesn't happen when my torrent client is closed and there isn't much traffic.

---

### Post by Peter09 on 2009-05-14
There is this bug

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291760](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291760)

the work around seems to be to install wicd

```
sudo apt-get install wicd
```

---

### Post by clownschoolphd on 2009-05-14
donato roque - I can't confirm an increase in occurrences with transmission open.  I rarely do any torrenting at work.  I have noticed an increase in drops with Pidgen open.  But thats anecdotal evidence at best.

Peter09 - I'll keep the wicd option in my back pocket but the bug report you reference seems to be more for wireless connections.  That bug also leaves evidence in /vat/log/daemon.log.  My daemon.log contains no information concerning the network drop.  It does show my reconnect actions after fixing the problem.

Appreciate the input and glad(?) to hear I'm not the only one experiencing this.

If anyone else has ideas, I'm all ears.

Cheers!

---

