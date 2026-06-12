---
title: "I can't get wireless IP"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by daniel4m on 2009-07-20
OK. My english is little bad. I have wireless card(Atheros chipset), TL-WN651G. Ubuntu 9.04 that i have recognize card.   
I have tried all methods with madwifi and ndiswrapper(with my WinXP drivers) but there is no the connection. I see networks but command ifconfig is suspicious to me. Here is the printout:

>>ifconfig
ath0      Link encap:Ethernet  HWaddr 00:21:27:db:41:b3 <-- my card MAC 
          inet6 addr: fe80::221:27ff:fedb:41b3/64 Scope:Link <-- here needs to bee IP and ...
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:03:47:0b:a8:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:13:d4:a8:b4:ff  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-21-27-DB-41-B3-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:105
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:6299 (6.2 KB)  TX bytes:736 (736.0 B)
          Interrupt:16 



My card is ath0 . If somebody now what is problem let me to know. Thanks:(

---

### Post by martinbaselier on 2009-07-20
I've neither used madwifi, nor ndiswrapper, but it would be helpful for others to know which method you choose at the moment. 

also the output of **iwconfig** would be interesting.

Do you use the graphical network manager to connect? 

Does your network have encryption (WEP/WPA/WPA2) if it does, which one?

Do you use dhcp on the network or static ip addresses?

---

### Post by daniel4m on 2009-07-21
> **martinbaselier said:**
> I've neither used madwifi, nor ndiswrapper, but it would be helpful for others to know which method you choose at the moment. 

also the output of **iwconfig** would be interesting.

Do you use the graphical network manager to connect? 

Does your network have encryption (WEP/WPA/WPA2) if it does, which one?

Do you use dhcp on the network or static ip addresses?

Here is output:
[B]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate: 0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry: off   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=0/70  Signal level=-90 dBm  Noise level=-90 dBm
          Rx invalid nwid:15962  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0[/B]

I tried madwifi and ndiswrapper but the same problem. I use gnome network manager(in the upper right corner). My network display Encryption key: off

---

