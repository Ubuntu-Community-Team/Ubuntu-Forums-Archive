---
title: "[SOLVED] Wireless Networking no longer working."
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by Jakey_TheSnake on 2009-01-09
Hi all, 

I am running Ubuntu 8.10 on the Acer Aspire One. 

I had my wireless working no problem for ages thanks to the guide here: [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

Using the latest madwifi driver and have ath_pci appended onto my /etc/modules. 

Suddenly it stopped working, I can only assume because of a recent update, seeing as I did not change any settings and there was one recently. 

Anyhow, I have failed thus far to get it working again, with a make clean and then fresh install.

I am completely at a loss of what to do. 

Please advise, 

- Jake


edit: this is the output of my "iwconfig"

```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

And this is the output of my ifconfig:

```
ath0      Link encap:Ethernet  HWaddr 00:23:4d:49:23:2f  
          inet6 addr: fe80::223:4dff:fe49:232f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1e:68:e4:83:b5  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fee4:83b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3544 errors:0 dropped:1830297737 overruns:0 frame:0
          TX packets:3063 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3853641 (3.8 MB)  TX bytes:499901 (499.9 KB)
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1824 (1.8 KB)  TX bytes:1824 (1.8 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-23-4D-49-23-2F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:14950 (14.9 KB)
          Interrupt:18 


```

---

