---
title: "No wireless since 1 week: output from islw -C network"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by nimonika on 2009-01-28
Please could someone help me trouble shoot this one. I have not be bale to connect to wireless for 1 week now

*-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 13
       serial: 00:13:a9:60:97:05
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=143.210.72.223 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:ad:46:07
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 82:12:39:ba:b3:d8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by theDaveTheRave on 2009-01-28
hi nimonica


You outpur of lshw seems to show everything is in order.

send a copy of the output of

```

iwlist scan
ifconifg

```

The first will show up if there is a network device that is able to see wireless networks, and if the device is "down" then it will simply say that the scan is unsuccessfull.

The second will show the full ip config for all the functioning interfaces.

I'm expecting some information about <wmaster0>

if there is and it says returns a load of bumpf on the <iwlist scan> command then try issuing

```

if up wmastero

```

and see what happens.

However, currently the link is "dissabled" and I'm not sure exactly why.

with this other information you may be able to find other threads that are more specific to your problem.

David

---

### Post by nimonika on 2009-01-31
Hello

iwconfig gives this:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      No scan results

pan0      Interface doesn't support scanning.

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:13:a9:60:97:05  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:a9ff:fe60:9705/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1037 errors:0 dropped:0 overruns:0 frame:0
          TX packets:986 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1110356 (1.1 MB)  TX bytes:200485 (200.4 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1624 (1.6 KB)  TX bytes:1624 (1.6 KB)

---

### Post by FishRCynic on 2009-01-31
ubuntu flavour is ?


are you using network manager?
if so right click and is:
enable networking  checked?
enable wireless    checked?

is the ethernet cable plugged in?
(it appears that the 88E8036 PCI-E Fast Ethernet Controller eth0 has an ip 192.168.0.2)

---

### Post by nimonika on 2009-01-31
Networking is checked and wireless is also enabled....

---

