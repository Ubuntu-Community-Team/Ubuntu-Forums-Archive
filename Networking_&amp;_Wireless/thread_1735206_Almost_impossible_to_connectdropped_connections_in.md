---
title: "Almost impossible to connect/dropped connections in Ubuntu 10.10"
date: 2011-04-21
forum: Networking &amp; Wireless
---

### Post by mjmckillop on 2011-04-21
I had the same problem as others did with the RaLink 5390 wireless device. I went through the process others have ([http://ubuntuforums.org/showthread.php?t=1645716]("http://ubuntuforums.org/showthread.php?t=1645716")) and this was successful in recognising the wireless device, but now networking is extremely difficult to establish, taking about half an hour of attempted connections, and these connections are also dropped.

Not sure at this stage if this is an Ubuntu problem or a router issue, as I'm not very proficient in Ubuntu. Any help would be greatly appreciated.

```
matt@matt-HP-G62-Notebook-PC:~$ lspci -nn | grep 'RaLink'
02:00.0 Network controller [0280]: RaLink Device [1814:5390]

matt@matt-HP-G62-Notebook-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 98:4b:e1:a3:89:8a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ra0       Link encap:Ethernet  HWaddr 90:00:4e:20:35:44  
          inet6 addr: fe80::9200:4eff:fe20:3544/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9798 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1560423 (1.5 MB)  TX bytes:0 (0.0 B)
          Interrupt:16 

matt@matt-HP-G62-Notebook-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: 00:22:75:CB:1F:49   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

matt@matt-HP-G62-Notebook-PC:~$ lsmod | grep 'rt5390sta'
rt5390sta            1172741  1 
cfg80211              144694  1 rt5390sta

matt@matt-HP-G62-Notebook-PC:~$ dmesg | grep 'rt5390sta'

matt@matt-HP-G62-Notebook-PC:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:22:75:CB:1F:49
                    Protocol:802.11b/g
                    ESSID:"Thompson"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:94/100  Signal level:-53 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 02 - .....

matt@matt-HP-G62-Notebook-PC:~$ lsb_release -d
Description:	Ubuntu 10.10

matt@matt-HP-G62-Notebook-PC:~$ uname -mr
2.6.35-28-generic i686

matt@matt-HP-G62-Notebook-PC:~$ sudo /etc/init.d/networking restart
[sudo] password for matt: 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface ra0=ra0.
                                                                         [ OK ]
```

---

### Post by mjmckillop on 2011-04-21
Managed to resolve this. When editing the blacklist.conf file to get RL5390 wireless card working, adding BOTH these lines resolves the issue:

blacklist rt2800pci
blacklist rt2860pci

---

