---
title: "Wake-on-LAN not working"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by Simon Cropper on 2011-05-31
Hi,

I have an old HP Netserver E60 that I am trying to run as a daily backup repository. I want to turn it on at set times, run rsync then close it down. I have set it up with Ubuntu Server 10.04 LTS. 

The blurb at the start login... "Linux netserver 2.6.32-21-generic-pae #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 i686 GNU/Linux Ubuntu 10.04 LTS"

The server is established and I can access the web from the server and 'ssh' into the server from another Ubuntu machine, _therefore the ethernet card is working_.

I am trying to get wake-on-lan to work but have found I can not get the server to wake regardless of the tutorial followed.

I have tried following...
[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)
[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_Wake-On-Lan_%28Ubuntu%29](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_Wake-On-Lan_%28Ubuntu%29)

All methods are essentially the same.

The problem is that regardless of what I do I can not get the server to wake up and I am now uncertain how I can troubleshoot the problem.

I have tried sending the magic packets with the python script mentioned in the second tutorial and every package listed in the Ubuntu Software Centre. I currently use Ubuntu 10.04 LTS on my desktop machine and I am using this to access the server.

Can someone point me to potential problems that might be happening?

Note...
1. That the 'network' is managed by a DHCP server on a D-Link DI-808HV Router not by Ubuntu Server.
2. I have installed xubuntu 10.04 LTS, Ubuntu Server 10.04 LTS and Ubuntu Server 11.04 on the E60 and the machine still does not wake-up, suggesting that it is either a problem with (a) the hardware [unlikely the manual indicates you can do this and options exist in the BIOS and the original built in network card is still present] or (b) the peer-to-peer network some how is filtering out the magic packet.
3. Yes, I have turned on 'wake-on-lan' in the E60 netserver BIOS.
4. I have closed down Ubuntu Server with 'shutdown -P now', 'halt' and 'poweroff' - the command used makes no difference.

**UPDATE -- **I have tried tracing the UDP packet and it appears to be discarded by the router (see results below). I can't see where such filtering would be happening as other UDP packets are getting through. 


[FONT="Arial Black"]The following details are relevant to the server being accessed...[/FONT]

COMMAND: **lspci -v** shows the following data about the network card...
--------------------------------------------------------------------------

00:06.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
        Subsystem: Hewlett-Packard Company Device 10ca
        Flags: bus master, medium devsel, latency 66, IRQ 19
        Memory at fc102000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 1800 [size=64]
        Memory at fc000000 (32-bit, non-prefetchable) [size=1M]
        [virtual] Expansion ROM at 10000000 [disabled] [size=1M]
        Capabilities: <access denied>
        Kernel driver in use: e100
        Kernel modules: e100

COMMAND: **ifconfig** shows the following details...
--------------------------------------------------------------------------

eth0      Link encap:Ethernet  HWaddr [removed]  
          inet addr:192.168.20.68  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fec2:daa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:413 errors:0 dropped:0 overruns:0 frame:0
          TX packets:247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41296 (41.2 KB)  TX bytes:56685 (56.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8904 (8.9 KB)  TX bytes:8904 (8.9 KB)

COMMAND: **sudo ethtool eth0** shows the following details...
--------------------------------------------------------------------------

	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: No
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: g
	Current message level: 0x00000007 (7)
	Link detected: yes

BIOS version 
--------------------------------------------------------------------------

PhoenixBIOS 4/06.18 PN


UDP Packet Delivery
-------------------------------------------------------------------------------------

Using **sudo tcpdump -i eth0 udp** on the server I get the following result when Magic packet sent by the desktop machine. UDP packet that is 126 long appears when ever wakeonlan xx:xx:xx:xx:xx:xx is used.

12:21:10.379039 IP 192.168.20.xx.33873 > 192.168.20.255.discard: UDP, length 126
12:21:16.919399 IP 192.168.20.xx.33219 > 192.168.20.255.discard: UDP, length 126
12:22:17.760336 IP 192.168.20.xx.35991 > 192.168.20.255.discard: UDP, length 126

I presume this means the router is discarding the magic packet and not delivering the information.

---

