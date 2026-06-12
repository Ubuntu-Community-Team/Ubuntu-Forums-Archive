---
title: "can't connect to wireless or ethernet on Netbook remix 8.10"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by ubigT on 2009-03-31
everything was working fine, I had my wireless working and was loving my new netbook.... then I messed up and did "sudo apt-get install samba"  upon realizing my mistake about 3 minutes later i did "sudo apt-get remove samba" but after that I could not connect to any networks, I can't even see any wireless networks now.
Did "sudo /etc/init.d/networking restart" and got this: 

*Reconfiguring network interfaces...                                                                                       Ignoring unknown interface ppp0=ppp0.

I checked out /etc/network/interfaces and it's just:

auto lo
iface lo inet loopback


So... any ideas on how to revive my networking capabilities? My Verizon USB727 works for internet, but nothing else.

---

### Post by ubigT on 2009-03-31
C'mon guys... someone has to have an idea!:confused:

---

### Post by BkkBonanza on 2009-03-31
Hmmm. Samba shouldn't have mucked up any wifi settings. 
Are you sure you didn't also do something else?

Post output from,

sudo ifconfig -a
and 
iwconfig

---

### Post by ubigT on 2009-03-31
I made no other changes in the time between my wireless working and it then dying. 

sudo ifconfig -a


> ath0      Link encap:Ethernet  HWaddr 00:23:4e:53:2f:de  
          inet6 addr: fe80::223:4eff:fe53:2fde/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:23:8b:28:64:a8  
          inet6 addr: fe80::223:8bff:fe28:64a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1879047824 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

pan0      Link encap:Ethernet  HWaddr 5e:60:08:ef:bf:2b  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:70.193.26.125  P-t-P:66.174.201.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1074 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1095 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1133619 (1.1 MB)  TX bytes:170907 (170.9 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-23-4E-53-2F-DE-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:339 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:15594 (15.5 KB)
          Interrupt:18 



and iwconfig:
> 
lo        no wireless extensions.

eth1      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ppp0      no wireless extensions.

---

### Post by BkkBonanza on 2009-03-31
Make sure your interface is up with,

sudo ifconfig ath0 up

Your info looks ok. If the interface is up then you should be able to use Network Manager to connect.

---

### Post by ubigT on 2009-03-31
that did it! thanks for the help :)

---

