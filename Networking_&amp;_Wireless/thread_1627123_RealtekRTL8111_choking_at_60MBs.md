---
title: "RealtekRTL8111 choking at 60MB/s"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by powel212 on 2010-11-21
How to get RealtekRTL8111 up to its full speed?

The built in ubuntu driver seems to be choked at 60MB/s

Is there a better driver for this chip?

On Mac and windows I can get the same chip to run over 100MB/s

Any help is appreciated.

powel

running Ubuntu 10.10 on GA-P43T-UD3L

---

### Post by powel212 on 2010-11-24
It is nice to see that people are looking at this thread. But no replies yet?

The realtek site seems to be down. Keep getting a redirect loop when I try to download their driver.

Anyone else having this issue?

Powell

---

### Post by cariboo on 2010-11-24
You can check connectivity speeds using iperf, which is in the repositories. There are also Windows and OSX versions availabale. Set up one system on your internal network as the server by typing:

```
iperf -s
```

then on another system on your internal network type:

```
iperf -c server name or ip address
```

you should get a result that should look something like this:

```
iperf -c willy
------------------------------------------------------------
Client connecting to willy, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.215 port 56380 connected with 192.168.1.250 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    113 MBytes  94.4 Mbits/sec
```

I have a 100Mbps network, so to me 94.4Mbps is an acceptable speed.

---

### Post by powel212 on 2010-11-24
@cariboo907:

Thanks for your info.

I tried it. Here is the result.

```
$ iperf -c 192.168.0.31
------------------------------------------------------------
Client connecting to 192.168.0.31, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.26 port 36990 connected with 192.168.0.31 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    496 MBytes    416 Mbits/sec
```

The same thing between 2 OSX computers with the same network hardware yields upwards of 896 Mbits/sec

Any thoughts on how I can get better performance?

Here is what ethtool has to report:

```
$ sudo ethtool eth4 
Settings for eth4:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  Not reported
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: No
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: umbg
	Wake-on: d
	Current message level: 0x00000007 (7)
	Link detected: yes

```

---

### Post by powel212 on 2010-11-26
Anyone know a mirror where I can download the realtek driver?

The website is FTP only.

I contacted Realtek today but seems like their Taiwan office is run by a bunch of monkeys.

P

---

### Post by powel212 on 2010-11-27
Found the Driver.

See attached.

Powel

---

