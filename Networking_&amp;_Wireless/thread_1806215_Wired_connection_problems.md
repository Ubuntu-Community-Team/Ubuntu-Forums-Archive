---
title: "Wired connection problems"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by dondada on 2011-07-17
My wired ethernet connection started acting funny last night. Browsing is slow or doesn't work at all. Interestingly, my torrents are still downloading. Closing my torrent client doesn't help browsing, though. I tried an online speedtest and the download speed test worked fine, showing my normal bandwidth, but the upload test failed completely. I'm also having trouble seeing my network shares on my server. I had a static IP but changed it to dynamic just to see if that would help, but no luck. When I go to check my connection information from the network icon at the top right, I get the error: No valid connections found!. However, as before, torrents are coming down fine, if a bit slow. All other devices on my network are fine, wired and wireless.

I'm running Natty on this PC.

Any help would be very much appreciated.

---

### Post by jmoorse on 2011-07-17
"Have you tried turning it off and on again?"

---

### Post by dondada on 2011-07-17
Yes, numerous times, PC and router, too. Unplugged and plugged cables, too.

---

### Post by jmoorse on 2011-07-17
Ok, never hurts to check that first :)

Can you please post the output of:

lspci | grep -i ether
ifconfig -a
dig [www.google.com](www.google.com)
traceroute 8.8.8.8 [omit second IP address for 'anonymity]

---

### Post by dondada on 2011-07-17
Thanks for your help. Here's what I got:

> lspci | grep -i ether
02:00.0 Ethernet controller: Intel Corporation 82573E Gigabit Ethernet Controller (Copper) (rev 03)

>  ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:e6:05:09:d4  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e6ff:fe05:9d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:294436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:255684 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:305135837 (305.1 MB)  TX bytes:23586419 (23.5 MB)
          Interrupt:16 Memory:d0080000-d00a0000 

eth1      Link encap:Ethernet  HWaddr 02:21:e9:12:4d:7c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:807 errors:0 dropped:0 overruns:0 frame:0
          TX packets:807 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:114800 (114.8 KB)  TX bytes:114800 (114.8 KB)


> dig [www.google.com](www.google.com) 

;<<>> DiG 9.7.3 <<>> [www.google.com](www.google.com)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 24750
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.google.com](www.google.com).			IN	A

;; ANSWER SECTION:
[www.google.com](www.google.com).		304276	IN	CNAME	[www.l.google.com](www.l.google.com).
[www.l.google.com](www.l.google.com).	209	IN	A	74.125.226.17
[www.l.google.com](www.l.google.com).	209	IN	A	74.125.226.16
[www.l.google.com](www.l.google.com).	209	IN	A	74.125.226.20
[www.l.google.com](www.l.google.com).	209	IN	A	74.125.226.19
[www.l.google.com](www.l.google.com).	209	IN	A	74.125.226.18

;; Query time: 2 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sun Jul 17 11:27:19 2011
;; MSG SIZE  rcvd: 142



> traceroute 8.8.8.8
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  DD-WRT310Nspin (192.168.1.1)  0.826 ms  0.806 ms *
 2  dsl-69-172-104-1.acanac.net (69.172.104.1)  43.921 ms  47.243 ms  50.091 ms
 3  66.49.255.185 (66.49.255.185)  51.130 ms *  53.135 ms
 4  66.49.255.246 (66.49.255.246)  58.850 ms  59.908 ms  62.641 ms
 5  * * gw-google.torontointernetxchange.net (198.32.245.6)  64.840 ms
 6  209.85.255.232 (209.85.255.232)  68.785 ms 216.239.47.114 (216.239.47.114)  54.324 ms  55.300 ms
 7  209.85.255.235 (209.85.255.235)  64.115 ms *  63.591 ms
 8  * 72.14.239.93 (72.14.239.93)  68.222 ms 209.85.249.11 (209.85.249.11)  68.318 ms
 9  * 72.14.236.200 (72.14.236.200)  68.708 ms  70.160 ms
10  72.14.232.21 (72.14.232.21)  71.878 ms 216.239.49.145 (216.239.49.145)  82.248 ms *
11  google-public-dns-a.google.com (8.8.8.8)  70.825 ms  69.366 ms  70.316 ms


---

### Post by jmoorse on 2011-07-17
Hmm, that all looks fine.  Do you have a second nic (eth1)?  Can you try that?

---

### Post by dondada on 2011-07-17
That's the weird thing. There is a eth1 listed but I only have one physical NIC. Maybe I'll crack it open and see if there's a second one in there. I got this PC from work and only added some RAM to it when I got it home.

---

### Post by jmoorse on 2011-07-17
Can you install ethtool 'sudo apt-get install ethtool' and provide output of ethtool -i eth0, ethtool -i eth1?

---

### Post by dondada on 2011-07-17
Output below:

> ethtool -i eth0
driver: e1000e
version: 1.2.20-k2
firmware-version: 1.0-7
bus-info: 0000:02:00.0

> ethtool -i eth1
driver: ipheth
version: 
firmware-version: 
bus-info: 1-8:4.2

---

### Post by jmoorse on 2011-07-17
Ok, that solves the mystery of eth1.  Looks like it is for iPhone tethering.

Back to the problem at hand:

1. Can you swap out the ethernet cable just to rule it out?  And swap to a different port on your router?
2. What does 'sudo ethtool eth0' show?
3. Does 'dmesg | grep -i eth' show anything of note?

---

### Post by dondada on 2011-07-17
Swapped out the cable and that seemed to fix things. I can actually post these replies from the PC in question. Here's the output of the latest commands:

> ethtool eth0
Settings for eth0:
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
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: off
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x00000001 (1)
			       drv
Cannot get link status: Operation not permitted


> dmesg | grep -i eth
[    0.700114] i2c-core: driver [adp5520] using legacy suspend method
[    0.700118] i2c-core: driver [adp5520] using legacy resume method
[    1.629681] e1000e 0000:02:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:16:e6:05:09:d4
[    1.629687] e1000e 0000:02:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.629702] e1000e 0000:02:00.0: eth0: MAC: 2, PHY: 2, PBA No: FFFFFF-0FF
[   18.996891] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.386675] ipheth 1-8:4.2: Apple iPhone USB Ethernet device attached
[   19.387498] usbcore: registered new interface driver ipheth
[   20.338947] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   36.762533] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   36.762541] e1000e 0000:02:00.0: eth0: 10/100 speed: disabling TSO
[   36.762773] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   47.024014] eth0: no IPv6 routers present

It doesn't seem to be getting gigabit speeds. Can that be from the cable?

---

### Post by jmoorse on 2011-07-17
It could be the cable (Needs to be cat5e or cat6, not just cat5), does your router/switch have gigabit ports?

---

### Post by dondada on 2011-07-17
Yes, my router has gigabit ports but the cable is just an old cat5. i'll need to get or make a new one to fit the run anyway. 

Thanks very much for your help, Jeff.

---

### Post by jmoorse on 2011-07-17
My pleasure, take care

---

