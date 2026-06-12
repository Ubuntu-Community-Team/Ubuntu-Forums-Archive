---
title: "Ethernet suddently stopped working for no apparent reason"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by randizzle on 2011-05-04
I am using Ubuntu 10.04

For no apparent reason that I can determine I came to my workstation this AM and found that my ethernet is no longer working. 

I rebooted and noted that my /etc/resolv.conf was now empty. 

I have two machines connected to the same router (the other is OS X) and that machine is experiencing no problems. 

When I boot the netspeed applet shows that I am disconnected, but when I check the preferences, I see that it is showing the status of the vboxnet0 interface (I am not even sure what that is).

Here is the results of ifconfig -a

```

eth0      Link encap:Ethernet  HWaddr 00:1f:c6:86:ef:f1  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2228 (2.2 KB)  TX bytes:2228 (2.2 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


.. and here is the contents of /etc/init.d/networking

```

auto lo
iface lo inet loopback

```

Any help would be greatly appreciated.

---

### Post by randizzle on 2011-05-04
I am not sure how it was removed but I had back to add to the end of my interfaces file:

auto eth0
iface eth0 inet dhcp

---

### Post by Iowan on 2011-05-04
I'm not familiar with vboxnet0 either. 
Check the settings in Network Manager... The lines you added to the interfaces file are doing what NM *should* - in olden days, NM wouldn't touch an interface defined in */etc/network/interfaces*.

---

