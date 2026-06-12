---
title: "is Network Manager or WICD  really necessary?"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by Oriana on 2009-08-28
Ubuntu 9.04 . 

I have been having problems with both Network Manager and WICD in that the gui doesn't show what's there - Network Manager applet just plain doesn't show anything, and WICD would tell me that every single hub for the massive wireless network at my school was a separate network - and force me to manually connect when I moved about underneath it. That means reconnect every time I wanted to access the internet, to oh, say, download the powerpoint for a class, or get on facebook, whatever. lol.

Anyway, the question I want to know is if either of these two goofies are really needed, since there's supposedly a "network daemon" that overrules them anyway, or will I have the same problems with that code? I only really read one brief reference to that, anyway, but it might explain why I was able to use firefox online after I purged Network Manager. Although, another explanation might be that the purge wasn't entirely successful (and I purged after I removed and there are still files related to network manager that it decided not to delete on my machine! Stupid. Shouldn't sudo apt-get remove network-manager have at least DISABLED it, at the very very least?? much less remove it entirely!) (I'm not frustrated at all, can you tell?)

Does somebody have a better solution for me? I'm willing to go command-line if necessary... but a GUI that displays networks and strengths would be nice.


sudo ifconfig returns:

```
eth0      Link encap:Ethernet  HWaddr 00:16:d4:8d:3f:03  
          inet6 addr: fe80::216:d4ff:fe8d:3f03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:970 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:367676 (367.6 KB)  TX bytes:468 (468.0 B)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2432 (2.4 KB)  TX bytes:2432 (2.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:e3:ab:7a:8a  
          inet addr:172.28.62.34  Bcast:172.28.63.255  Mask:255.255.254.0
          inet6 addr: fe80::216:e3ff:feab:7a8a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89570 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:74624878 (74.6 MB)  TX bytes:10053451 (10.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-E3-AB-7A-8A-61-38-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

