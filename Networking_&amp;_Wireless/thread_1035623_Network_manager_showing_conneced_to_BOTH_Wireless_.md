---
title: "Network manager showing conneced to BOTH Wireless and NIC card"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by firstc624 on 2009-01-09
ok i have been fighting w/ my pc for a few days or 2 weeks now.  for some reason i am showing network manager being connected to BOTH my wireless nework and my ethernet port.

I do have my ethernet plugged in, but in the past it would only connect for one or the other, not try to both be on at the same time.  I do not have any idea what this is from..   here is the outpus of "ifconfig though

[HTML]firstc624@firstc624-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:37:18:94:ad  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:37ff:fe18:94ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:767 errors:0 dropped:0 overruns:0 frame:0
          TX packets:582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:687275 (687.2 KB)  TX bytes:118580 (118.5 KB)
          Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:00:ac:2b  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fe00:ac2b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:382 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68063 (68.0 KB)  TX bytes:4872 (4.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-00-AC-2B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/HTML]


Has anyone else had this problem?  

I am running Intrepid w/ all updates that have been available.  Thanks again.  if you need any other info just ask and i will post it up.

---

### Post by cwbar_1 on 2009-01-09
Right click on the network icon. Edit connections. Click on wired or wireless tab, (whichever one you do not want to connect with) click edit and untick the "connect automatically" box. I don't remember having to do this in previous network manager versions.  (I usually installed WICD)

---

