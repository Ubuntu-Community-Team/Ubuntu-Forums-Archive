---
title: "Broken Wireless connection"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by L0G0S on 2009-01-06
Hey all,
I recently installed Ubuntu 8.10 on my T61 alongside Vista...  It works perfectly except that the wireless is not working (Vista is fine, but I am reluctant to boot to it).  I've spent the better part of a month trying to find out how to enable it, but haven't had much luck so far.  



Here is my wireless info:
Card: Atheros ar5212

ifconfig
zais@zais-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:25:be:3a:d6  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:febe:3ad6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6637 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:6301477 (6.3 MB)  TX bytes:1157862 (1.1 MB)
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3284 (3.2 KB)  TX bytes:3284 (3.2 KB)

lspci -v
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
	Subsystem: IBM Device 058a
	Flags: fast devsel, IRQ 17
	Memory at df2f0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath5k, ath_pci

For some reason this command doesn't seem to give me the feedback that it previously gave me.  It used to say the only the ath_pci was in use...  I
could have blacklisted the ath_pci in my search for wireless vindication.  In which case, all that I would need to do is to properly install the ath5k...

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



My working theory at this point is that I need to enable the ath5k driver...  any help on how to do this would be appreciated...  Of course I could be mistaken (always possible, I am completely new to Linux).
Thanks in advance

---

### Post by L0G0S on 2009-01-06
I just rebooted this morning, and the outputs from a few commands seem to have gone back to normal.

zais@zais-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:22133  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


zais@zais-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1f:e2:86:5e:0e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1c:25:be:3a:d6  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:febe:3ad6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9353 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9098 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:10133598 (10.1 MB)  TX bytes:1476557 (1.4 MB)
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-1F-E2-86-5E-0E-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39916 errors:0 dropped:0 overruns:0 frame:5702
          TX packets:1076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:3318590 (3.3 MB)  TX bytes:45737 (45.7 KB)
          Interrupt:17 


lspci -v
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
	Subsystem: IBM Device 058a
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at df2f0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath_pci
	Kernel modules: ath5k, ath_pci

Again, I think that my problem is with this last output shown here...  I would like the ath5k to be the kernel driver in use, not the ath_pci.

---

### Post by L0G0S on 2009-01-08
Anyone?  This is really starting to bug me..

---

### Post by L0G0S on 2009-01-08
Anyone?  This is really starting to bug me..

---

