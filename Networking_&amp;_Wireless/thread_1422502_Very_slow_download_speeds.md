---
title: "Very slow download speeds"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by brokenbynubs on 2010-03-05
Hello all,

I've recently installed Ubuntu 9.10 and I'm having a pretty annoying problem with any sort of downloads that are outside of my browser - Chrome.  When I do any sort of update with Terminal, package manager or software center the download speeds start out fine(190Kbp/s) and then slowly nosedives into the B/s range... usually around 2200B/s.  This can be really annoying as it took me nearly 24 full hours to get the Ubuntu 9.10 updates from the server.  I've also ran the "select best server" option and the best one for me is missing 90% of the packages I need to download, unfortunately.  I tried the next closest one and it was still just as slow as the Main Server.

Now, that isn't saying that my browser doesn't suffer....  Usually if I download anything under 10mb I'm fine, but if it's a bigger file my speeds will dive down around 10-20Kbp/s.

I've ran all of the updates that Ubuntu wants, done apt-get update, apt-get upgrade.  Here is the results of my ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:22:15:b6:72:90  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:137997 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99564 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:160923652 (160.9 MB)  TX bytes:11345478 (11.3 MB)
          Interrupt:27 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 B)  TX bytes:300 (300.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:18:e7:54:d5:14  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-E7-54-D5-14-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

And here's sudo ethtool eth0:

```

Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

```

Thanks in advance.

---

### Post by brokenbynubs on 2010-03-05
Anyone at all?  This really is an OS-breaker.

---

### Post by brokenbynubs on 2010-03-06
Bump.

---

### Post by brokenbynubs on 2010-03-07
I've had this same problem for over a year.  Nobody was able to help me then, and nobody will even try to help me now.  Guess even though I've tried Ubuntu on 4 different computers and 6 different router/modem configurations it must just be me.

Oh well, back to Windows....

---

### Post by thesenu on 2010-03-25
you should use kget or wget application

---

