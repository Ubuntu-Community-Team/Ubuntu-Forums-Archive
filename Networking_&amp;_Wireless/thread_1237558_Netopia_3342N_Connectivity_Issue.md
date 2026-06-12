---
title: "Netopia 3342N Connectivity Issue"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by subxinu on 2009-08-11
I have a Netopia 3342N pocket USB modem that works great under Win XP; I only had to plug it in and it worked. It was previously configured with username/password.
 
After installing Ubuntu and plugging in the USB modem I get the following under the network conenctions:
 
> Wired Network (Unknown USB Communications Inferface)
 
I was initially excited as it seemed to be working just as it did under XP (machine is dual-boot) but, after opening Firefox, I cannot access the internet. I cannot ping out even. I found the "[access runner]("http://accessrunner.sourceforge.net/index.shtml")" website, but it seems antiquated as Ubuntu recognized the modem (albeit as "unknown").
 
Any suggestions?
 
Thanks!

---

### Post by subxinu on 2009-08-11
Anyone?

---

### Post by subxinu on 2009-08-12
```
me@ubuntu-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:Xc:6e:X7:f9:Xf   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:20 Base address:0xa400  
 
eth1      Link encap:Ethernet  HWaddr 00:Xf:cc:X3:7f:X5   
          inet6 addr: fe80::20e:ccfe:fea3:7e55/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:302 dropped:0 overruns:0 frame:302 
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:8713 (8.5 KB) 
 
eth1:avahi Link encap:Ethernet  HWaddr 00:Xf:cc:X3:7f:X5   
          inet addr:169.XXX.X.XX  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1054 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1054 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:54596 (53.3 KB)  TX bytes:54596 (53.3 KB) 
 
me@ubuntu-desktop:~$
```
 
Some of the addresses have been edited for anonymity. [IMG]http://eltworld.net/forums/images/smiles/icon_wink.gif[/IMG] 
 
As can be seen above: I have an inet address for the USB modem at eth1; I just can't reach the internet.

---

