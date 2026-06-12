---
title: "HP Pavillion dv1000 wireless key will not turn on"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by gonsalvr on 2009-03-22
I just wrote a post and I'm not sure where it went, so I apologize if it shows up twice.  
I'm a 4 day old Ubuntu n00b and have been trying to get my wireless key to turn on so I can connect to my wireless network. Last weekend my daughter came in and showed me her BSOD on Win XP and after trying to fix it, she had a corrupted MBR. I decided to wipe her drive and do a clean install of Ubuntu 8.10 from the download iso.  Since Friday I have been reading and googling to find a solution to my problem and "I Think" it is outside the kernel and I need to install the HP Pavillion dv1000 drivers for the network card.
Ubuntu network manager see's my wireless network and asks for the pass phrase, tries to connect then cancels out.  Below are network stats:

  eth0      Link encap:Ethernet  HWaddr 00:c0:9f:df:1c:a9  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fedf:1ca9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2743 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2819877 (2.8 MB)  TX bytes:340284 (340.2 KB)
          Interrupt:16 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr 00:15:00:1c:fa:ce  
          inet6 addr: fe80::215:ff:fe1c:face/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9435 errors:59 dropped:59 overruns:0 frame:0
          TX packets:1044 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5568 (5.5 KB)
          Interrupt:18 Base address:0x2000 Memory:b0107000-b0107fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

cmg@cmg-laptop:~$ 
cmg@cmg-laptop:~$ sudo ifconfig -s
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0      2743      0      0 0          2186      0      0      0 BMRU
eth1       1500 0     15656     59     59 0          1693      0      2      0 BMU
lo        16436 0         2      0      0 0             2      0      0      0 LRU


cmg@cmg-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ls -1
Desktop
Documents
Examples
HP Wireless Key On
HP Wireless Key On~
Music
Pictures
Public
Templates
Videos

After rooting around you can see Ubuntu is finding my wireless network, so how do I turn it on.

After two days of reading, and googling I have two options:
1. Open the back ports
2. Install HP Pavillion dv1000 drivers 

Not sure what direction to take and if they will even solve my problem.
Any guidance  will be greatly appreciated. Spring break is over and my daughter wants her laptop back but she really needs the mobility of wireless connectivity.

Thanks,
gonalvr

---

### Post by gonsalvr on 2009-03-23
Forum, Ok I had one of the guy's at work who is well versed in Linux and he said it all looks good to him. The HP wireless key switch is probably HP specific.  So I came home and turned off my WEP and voila I'm currently online wirelessly using Ubuntu.  So now my dilemma is how do I get my Ubuntu configuration to link using WEP.

Any Thoughts I'm listening, in the mean time I'm still researching and learning. 

gonsalvr

---

