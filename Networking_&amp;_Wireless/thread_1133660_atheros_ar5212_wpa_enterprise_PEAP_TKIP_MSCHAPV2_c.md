---
title: "atheros ar5212 wpa enterprise PEAP TKIP MSCHAPV2 connection issue"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by Ryuhayabusa on 2009-04-23
Dear forummers,

I am able to connect to my home 'personal' wpa using a psk-pre shared key.

but when i try to connect to the university network which uses an i.d and password I can 'see' the network, i get a signal, i get an ip by dhcp 'avahi' thingo's. but i cannot get any webpages etc.

I am using nm-applet.

I think i may be over my head.

the settings for the uni network are 

WPA enterprise PEAP TKIP MSCHAPV2 

i can see the network 
```

sunil@gman:~$ sudo iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"uniwide"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:4A:32:9D:11   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=20/70  Signal level=-75 dBm  Noise level=-95 dBm
          Rx invalid nwid:2237  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

and i do a dhclient to try to get an address. I don't have to do that at home. But it wasn't working so i tried it.

```


sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:17:9a:02:5d:9e
Sending on   LPF/ath0/00:17:9a:02:5d:9e
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Listening on LPF/eth0/00:00:e2:8c:71:e5
Sending on   LPF/eth0/00:00:e2:8c:71:e5
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

after that i seem to get an address. 

```


 ifconfig 
ath0      Link encap:Ethernet  HWaddr 00:17:9a:02:5d:9e  
          inet6 addr: fe80::217:9aff:fe02:5d9e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:26 dropped:26 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:520 (520.0 B)  TX bytes:5311 (5.1 KB)

ath0:avahi Link encap:Ethernet  HWaddr 00:17:9a:02:5d:9e  
          inet addr:169.254.5.220  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:00:e2:8c:71:e5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0:avahi Link encap:Ethernet  HWaddr 00:00:e2:8c:71:e5  
          inet addr:169.254.9.166  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:934 errors:0 dropped:0 overruns:0 frame:0
          TX packets:934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46700 (45.6 KB)  TX bytes:46700 (45.6 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-17-9A-02-5D-9E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9488 errors:0 dropped:0 overruns:0 frame:26777
          TX packets:265 errors:1 dropped:26 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1719194 (1.6 MB)  TX bytes:16554 (16.1 KB)
          Interrupt:11 

```

but after that I cant ping any webpages. The RX count for wifi continues to go upward for ever though.

```

sunil@gman:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 ath0
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 ath0
sunil@gman:~$ ping www.unsw.edu.au

```

I don't have much understanding of what is going on.

any help much appreciated. 

I also tried wicd, the same thing happened really, IP address but no way to webpages.

Any help much appreciated.

Thanks

---

### Post by Ryuhayabusa on 2009-04-23
by the way i'm using 8.04lts 2.6.24 kernel.

---

### Post by Ryuhayabusa on 2009-04-23
actually i'm not supposed to have two ip addresses am i.

but there was no cable in the ethernet port, i dunno why dhclient put an ip address for the eth0 one.

---

### Post by Ryuhayabusa on 2009-05-15
an update on my meagre progress.

I have now upgraded to jaunty. I was unable to connect using ath5k or madwifi drivers and network-manager applet. I was able to connect to wep at home but not wpa enterprise at university

I have switched to wicd (which i think has a more 'transparent' interface because it uses wpa-supplicant configuration files?)

I have installed ndiswrapper and am using the 2kxp driver from the dlink australia website for my revision c card. It seems to be working well.

Next time at uni i will try ndiswrapper and wicd,

wicd and madwifi.

I will not try ath5k as i think that there are some bug reports saying that this driver is not working for enterprise.

Wish me luck?

thanks guys who make ndiswrapper and all the other drivers too!

if i get it to work i'll try to make a good guide.

---

### Post by Ryuhayabusa on 2009-07-20
i have successfully connected with an r51 using ipw2200 driver.

I would recommend that people 'try before they buy' wireless cards to avoid the hassle of driver fustration.

---

