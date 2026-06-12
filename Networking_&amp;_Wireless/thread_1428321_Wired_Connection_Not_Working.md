---
title: "Wired Connection Not Working"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by Calorus on 2010-03-12
Hello All,

I've not changed my configuration, but after temporarily unplugging my laptop from the router, I can no longer persuade it to connect again.

Have restarted it repeatedly, but to no avail.

A similar problem has been occurring with my Huawei 3G Dongle which has suddenly started behaving.

Are there any troubleshooting guides for the Network Manager's wired connections? Don't know where to start...

---

### Post by Iowan on 2010-03-12
Restart or reboot? (If restart - what service(s) did you restart?)

---

### Post by Calorus on 2010-03-12
Both, I killed the NM-Applet and restarted that, and then rebooded the machine after that gave me no joy.

Have Rebooted 3 times to no avail.

---

### Post by Iowan on 2010-03-12
A couple of things to check (both from terminal). **ifconfig -a** should show if the machine gets an IP address. **[B]sudo lshw -C network**[/B] should show status of interface with drivers, etc.

---

### Post by Calorus on 2010-03-12
ifconfig -a yields:

 eth0      Link encap:Ethernet  HWaddr 00:1f:16:15:a6:1f  
          inet6 addr: fe80::21f:16ff:fe15:a61f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:972 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:79824 (79.8 KB)  TX bytes:4914 (4.9 KB)
          Memory:f2600000-f2620000 

And lshw -C network:

*-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1f:16:15:a6:1f
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.8-3 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:f2600000-f261ffff memory:f2625000-f2625fff ioport:1840(size=32)


__

To describe the visible symptoms a little more: the NM-applet shows as trying to make a connection, then fails out...

---

### Post by Iowan on 2010-03-12
Since no IP address shows - I presume DHCP is failing... Unfortunately, brain (mine) is not hitting on all cylinders tonight...

---

