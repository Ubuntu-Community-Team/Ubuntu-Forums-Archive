---
title: "Wireless Network &quot;Stalling&quot;"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by sceazy on 2009-04-10
I seem to have this problem using wireless on my laptop.  I know that the problem affects me on both Ubuntu 8.10 and 9.04(so far), and seems to affect all the varients.  Whenever I try downloading something large, after awhile the download will stall for, often over a minute, then resume.  
This happens in firefox, when downloading files, with synaptic, when downloading packages or sometimes when reloading the sources, and when using subversion.  I can still use the network while something is stalled... so it seems to just stall that specific connection.  I have another computer on the same network, using ubuntu, with a wired connection, and it doesn't suffer from the same problem, so I'm assuming its a wireless problem... 
I'm on a HP Pavilion dv5-1010, and aside from this, everything else seems to work fine with ubuntu...  Any ideas?

Edit:
Oh and this problem seems to have made subversion next to useless seeing as when it stalls if tends not to resume, unless that is a different problem, but I would think the two would be related.

---

### Post by superprash2003 on 2009-04-11
post output of **ifconfig** from the terminal.Your MTU values maybe too low.

---

### Post by sceazy on 2009-04-11
Here is the output from ifconfig...
```

eth0      Link encap:Ethernet  HWaddr 00:1e:68:b6:c5:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:247 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1248 (1.2 KB)  TX bytes:1248 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:ea:ad:22:f0  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:eaff:fead:22f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1522 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1366 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1592835 (1.5 MB)  TX bytes:300039 (300.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-EA-AD-22-F0-32-66-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

