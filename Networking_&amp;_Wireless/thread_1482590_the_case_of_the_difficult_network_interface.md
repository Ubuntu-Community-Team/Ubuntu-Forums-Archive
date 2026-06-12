---
title: "the case of the difficult network interface"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by fr33loder on 2010-05-13
Hi all.

Have recently installed lucid server, and all was proceeding reasonably well until this morning.

I have lost the ability to access the server via the eth0 interface - fortunately, I have 2 active intefaces connected to the router, so I have an alternative.

Below is the output from ifconfig (MAC Addresses removed)

```

eth0      Link encap:Ethernet  HWaddr 00:1a:4d:45:74:c9  
          inet addr:192.168.0.52  Bcast:192.168.0.127  Mask:255.255.255.128
          inet6 addr:XXX Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:987 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:154662 (154.6 KB)  TX bytes:13591 (13.5 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1a:4d:45:74:d9  
          inet addr:192.168.0.53  Bcast:192.168.0.127  Mask:255.255.255.128
          inet6 addr: XXX Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:243705 (243.7 KB)  TX bytes:427646 (427.6 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

```I can see no difference in the configuration of the two interfaces, and the DHCP from the router still assigns an ip, but the eth0 interface does not respond to internal pings, cannot be used for ssh etc.

any help would be GREATLY appreciated.  the only thing I've done this morning to change anything is to add a wakeonlan config script.

---

### Post by sir_nasty on 2010-05-13
will eth0 respond if you ping it from the servers command prompt?

---

### Post by fr33loder on 2010-05-13
> **sir_nasty said:**
> will eth0 respond if you ping it from the servers command prompt?

yes - it does.  And I have also just discovered that cycling the interface (ie. ifdown then ifup) seems to, occasionally, resolve the issue, although it returns on reboot

thx!

---

