---
title: "Network Performance diff: 2 identical hardware boxes"
date: 2010-08-16
forum: Networking &amp; Wireless
---

### Post by r m h on 2010-08-16
I have 2 identical Dell Optiplex 160s 4GB RAM, Dual Core 1.6GHz atom running 64 bit Ubuntu.  

Both of these Optiplex machines are wired to the same managed switch.

The Jaunty Gbit NIC runs almost 100x faster than the Lucid NIC (748 Mbits/s vs 9.4 Mbits/s), yet they are both running at Gbit speeds according to ethtool and the switch.

If I reverse the iperf client and server (have my workstation run the server and the Optiplex boxes run the clients), there is no change in throughput.

Workstation running iperf client -> Netgear GS724T 24port managed switch -> both Optiplexs running iperf server

Anyone care to reason why, or help keep me from pulling what little hair I have left out of my head?



The Jaunty Optiplex box:
root@nagios01:~# cat /etc/lsb-release
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

```

root@nagios01:~# uname -a
```
Linux nagios01 2.6.28-19-server #61-Ubuntu SMP Thu May 27 00:22:27 UTC 2010 x86_64 GNU/Linux

```

root@nagios01:~# ethtool eth0
```
Settings for eth0:
	Supported ports: [ TP ]
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
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Current message level: 0x000000ff (255)
	Link detected: yes

```

The Lucid Optiplex box:
root@pico:/etc# cat /etc/lsb-release
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

```

root@pico:/etc# uname -a
```
Linux pico 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

```

root@pico:~# ethtool eth0
```
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  Not reported
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: No
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: g
	Wake-on: g
	Current message level: 0x000000ff (255)
	Link detected: yes

```

Using iperf-3.0b4 ($ iperf3 -s -i 1 -p 5001 -f m)
The Jaunty box shows a throughput of:
```
      Sent
[  5] 0.00-30.03 sec  2.61 GBytes   747 Mbits/sec
      Received
[  5] 0.00-30.03 sec  2.61 GBytes   746 Mbits/sec

```

The Lucid box shows a throughput of (but peaks at 12.5 Mbits):
```
      Sent
[  5] 0.00-32.47 sec  36.4 MBytes  9.40 Mbits/sec
      Received
[  5] 0.00-32.47 sec  36.4 MBytes  9.40 Mbits/sec

```


I have tested iperf from my workstation through the same Netgear managed switch connected to a second Netgear GS724T managed switch to a custom 4U server running 64-bit Lucid (Dual 3.0GHz Xeons, 8GB RAM).  

$ uname -a
```
Linux iceax 2.6.32-22-server #36-Ubuntu SMP Thu Jun 3 20:38:33 UTC 2010 x86_64 GNU/Linux
```

# ethtool eth0
```
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  Not reported
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: No
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: g
	Wake-on: g
	Current message level: 0x000000ff (255)
	Link detected: yes

```

iperf client on my workstation tells me that this connection runs at speeds 200Mbits/s faster than the fastest Optiplex speeds:
```
      Sent
[  5] 0.00-30.06 sec  3.29 GBytes   940 Mbits/sec
      Received
[  5] 0.00-30.06 sec  3.29 GBytes   940 Mbits/sec

``` 

Thanks

---

