---
title: "Losing internet connection in Ubuntu Studio 9.10"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by Piffilus on 2010-01-26
I think I would begin to say that I'm kind of noob with manageing network in linux, well I have used ubuntu intermittently since 7.04 but had some problems that has gotten overwhelming and I've reluctantly fallen back to windoze because I really like ubuntu a whole lot more when it works as I want it too.

I have a tricky problem that I don't understand why it happens and how to solve it. I've had Ubuntu Studio 9.10 dual booting with Windoze Vista for a while now and I'm very satisfied with U.S.9.10 until a couple of days ago when it suddenly didn't let me connect to internet or just for a couple of minutes at most though I can ping and open my router in Firefox. Sometimes the connection comes back for a minute or two and then drops it again. What I think is weird is that I can connect to internet with Vista and Ubuntu 9.10 Live-CD and there are no problems at all with losing connection. I use DHCP and have changed to static IP and back again, reset the router but nothing helps.

I have run ifconfig in Ubuntu Studio and the outcome is:

```
piffen@piffen:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:87:5f:8e  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::21f:c6ff:fe87:5f8e/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:1257 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1199 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:385789 (385.7 KB)  TX bytes:143122 (143.1 KB) 
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:262175 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:262175 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:13111652 (13.1 MB)  TX bytes:13111652 (13.1 MB) 

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:02:49:8f  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::21f:3cff:fe02:498f/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:2091 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1111 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:891645 (891.6 KB)  TX bytes:176978 (176.9 KB) 

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-02-49-8F-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

```

If I run ifconfig on Ubuntu Live-CD the outcome is:

```
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:87:5f:8e  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fe87:5f8e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:726 errors:0 dropped:0 overruns:0 frame:0
          TX packets:777 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:872260 (872.2 KB)  TX bytes:66485 (66.4 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:02:49:8f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-02-49-8F-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I find this very annoying because I'd rather use my Ubuntu Studio than Windoze. I want to back up my settings and applications I have installed and wanted to install the 'sbackup' package but it is impossible since I can't connect to the repositories to do that. I'm not really sure what directories to backup either. Is /home all that is needed to restore all my settings and applications if I can't resolve this network problem and go crazy and decide to make a clean reinstallation of Ubuntu Studio, which I hope I don't need to do in the first place?

I have made a /home partition on an external sata disk where I thought I could put my backup in and I wonder if this is the way to go or should I have such a partition on the internal disk?

---

