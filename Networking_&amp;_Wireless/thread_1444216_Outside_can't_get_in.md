---
title: "Outside can't get in"
date: 2010-04-01
forum: Networking &amp; Wireless
---

### Post by p2ranger on 2010-04-01
Today put in a new gigabit NIC in my server as the integrated interface was 10/100. I just tried accessing my server from the outside world and I can't get to it. I'm stuck on where to begin looking for my problem.

Originally the integrated network interface was working fine on eth0. I installed the new NIC and it is shown as eth1. I had been using a static IP for eth0 which was 192.168.1.120. I changed that to go to the new NIC and the old interface now has a static IP of 192.168.1.119

Below is the contents of my ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:22:68:6d:37:b9  
          inet addr:192.168.1.119  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:68ff:fe6d:37b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14581 (14.5 KB)  TX bytes:4851 (4.8 KB)
          Interrupt:253 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:1b:21:50:71:05  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:21ff:fe50:7105/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32014 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2903250 (2.9 MB)  TX bytes:934351 (934.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:621 errors:0 dropped:0 overruns:0 frame:0
          TX packets:621 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:308105 (308.1 KB)  TX bytes:308105 (308.1 KB)

virbr0    Link encap:Ethernet  HWaddr fa:7d:d8:22:aa:17  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::f87d:d8ff:fe22:aa17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:797 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:388605 (388.6 KB)


```

Below is the contents of my /etc/network/interfaces

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto eth0
iface eth0 inet static
        address 192.168.1.119
        netmask 255.255.255.0
        gateway 192.168.1.1

auto eth1
iface eth1 inet static
        address 192.168.1.120
        netmask 255.255.255.0
        gateway 192.168.1.1

```

I've tried restarting the computer, and the router. I've tried doing my port forwarding to both 119 and 120. I can ping google from the command prompt, but can't get into the computer.

Still learning my way around linux. Any thoughts would be great.

Thanks

Jason

---

### Post by p2ranger on 2010-04-01
Update, well, I think I found part of a solution. I have my new NIC plugged into a gigabit switch that I bought. I had the old network interface also plugged into this switch. I unplugged the old interface and put this into the 10/100 router I have (where the switch is plugged into) and I can get the outside world to see now. But this seems like a strange fix. Any ideas?

Thanks

Jason

---

### Post by Iowan on 2010-04-01
Having both interfaces in the same subnet will likely cause problems (and violates some standard I can't name at the moment...). You should be able to edit */etc/udev/rules.d/70-persistent-net.rules* to make whichever interface you wish be eth0. If you don't need the other one, omit (comment out) the "auto" line.

---

### Post by Junglizer on 2010-04-02
Sweet! I'm in Iowa too! [not really related in the slightest to this topic]

---

