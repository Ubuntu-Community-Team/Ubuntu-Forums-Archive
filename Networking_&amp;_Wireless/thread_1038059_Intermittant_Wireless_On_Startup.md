---
title: "Intermittant Wireless On Startup?"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by ToyotaGuy23 on 2009-01-12
Sometimes after bootup, Network Manager doesn't show any wireless networks available.  If I restart, **usually** the problem is solved, although not always.  

My System:  
DELL Inspiron 1721
Ubuntu 8.10 Intrepid Ibex
2.0 Ghz AMD
2 GB DDR 2
250 GB HD
Dell 1505 802.11 n
Broadcom 4328 10/100

Here is all the information that I can provide when the problem is happening:

I ran **iwconfig**:
lo   no wireless extensions
eth0 no wireless extensions
pan0 no wireless extensions

Why is there no wlan0?  

I ran **sudo ifconfig wlan0 up**:
wlan0: Error while getting interface flags: No such device

I ran **lshw -C network**:
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:af:31:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b6:bd:cb:02:b6:24
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

I ran** ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:1d:09:af:31:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:326 errors:0 dropped:0 overruns:0 frame:0
          TX packets:326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26136 (26.1 KB)  TX bytes:26136 (26.1 KB)

---

### Post by ToyotaGuy23 on 2009-01-13
bump? 

help?

---

### Post by ToyotaGuy23 on 2009-02-03
Here is the solution:

I had a 'race' condition.
This means that the b43 driver and ndiswrapper were competing for the connection.  

Thanks to Sylphid in the IRC, I successfully did this and it worked!

I compared the output of **lshw -C network** from when it was working and when it was not.  That is how the 'race' condition was discovered.  Thanks, Sylphid! 

So we needed to blacklist the b43 because it was unreliable on my system.
```

matt@matt-laptop:~$ sudo -i
[sudo] password for matt: 
root@matt-laptop:~# echo 'blacklist b43' >> /etc/modprobe.d/blacklist
root@matt-laptop:~# exit
```

---

