---
title: "Network settings help"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by Pflumberg on 2009-05-05
I am having trouble with ethernet access since I upgraded to Ubuntu 9.04.  I can access my computer from off site using ftp clients like I always could, but I cannot get any internet activity from that computer and can't access any sites or update.  Any ideas?

Let me know what information will be helpful to answer this and I will get it up as soon as I can.

Thanks in advance for the help.

Josh

---

### Post by Iowan on 2009-05-05
Post results of **ifconfig -a**, and **lshw -C network**

---

### Post by Pflumberg on 2009-05-06
Here are the results that I get from ifconfig -a and lshw -C network.  I did notice that it says network DISABLED when I did lshw -C network, but I am not sure if that makes a difference or how to change that.  Again, thanks for the help.

ifconfig -a gives
eth0      Link encap:Ethernet  HWaddr 00:30:1b:ae:61:cc  
          inet addr:10.0.1.214  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:feae:61cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65937 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15453 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8273623 (8.2 MB)  TX bytes:2300443 (2.3 MB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:903 errors:0 dropped:0 overruns:0 frame:0
          TX packets:903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77874 (77.8 KB)  TX bytes:77874 (77.8 KB)

pan0      Link encap:Ethernet  HWaddr de:d7:01:49:d0:93  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lshw -C network gives
  *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: a1
       serial: 00:30:1b:ae:61:cc
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=10.0.1.214 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:d7:01:49:d0:93
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Pflumberg on 2009-05-07
Also, because of all of this I am unable to do any updates or get access to the internet.  

Thanks in advance for the help.

---

