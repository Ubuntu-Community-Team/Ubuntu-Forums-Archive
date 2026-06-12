---
title: "connect at work; can I get all network info from Windows?"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by ClarkePeters on 2010-03-08
dual boot on Hardy Heron on HPlaptop

Hi all,
I'm trying to get my computer connected to the internet at work.
I live in Taiwan, don't speak Chinese, as well, the network administrators (through an interpreter) say they know nothing about how to set up a connect in ubuntu or any other Linux system. So I'm completely on my own.

I went into windows to get my IP address, subnet Mask, gateway address, and DNS server. I put these in using sys>admin>network>wired connect | dns.

Nothing works. I went to Network Tools and tried to ping the dns server and another address given from the Ubuntu help menu. Nothing.

In network tools, I see two options under devices, loopback interface and ethernet (eth0).  I can't do anything with loopback and it has the standard 127.0.0.1  255.0.0.0 showing (shadowed).
So i skipped that and then clicked on the ethernet option and the "configure" button becomes active. The ip and such that I put in seem to be showing there, but when I click on "configure" I get 
something like "The interface doesn't exist"  

the network proxy setting is "direct internet connection"


Seems that since I can connect when in Windows, I ought to just be able to get all the information I need and set it all up in Ubuntu.

Can anyone please direct me? Maybe I don't have enough info from Windows, and maybe I'm not putting things in the right places in Ubuntu. I won't be in the office till tomorrow, but in the meantime, any suggestions appreciated, and I'll be happy to get any info from files from either system and post them if I can just get some direction.

Thank you very much.

---

### Post by ClarkePeters on 2010-03-08
b

---

### Post by chili555 on 2010-03-08
Do you actually have a working ethernet interface? Please open a terminal and do:```
ifconfig
```Is there an interface there, eth0, perhaps? If so, please post:```
sudo ethtool eth0
```If not, please post:```
lspci -nn | grep Ether
```Thanks.

---

### Post by ClarkePeters on 2010-03-10
Thanks chili555
here is the info from ifconfig and ethtool (overwrote some address numbers with # for security reasons):
```

====== ifconfig infon==========
eth0      
Link encap:Ethernet  HWaddr 00:25:b3:7d:##:##  
          
inet6 addr: fe80::225:b3ff:fe7d:c##a/## Scope:Link          
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1          
RX packets:429 errors:0 dropped:0 overruns:0 frame:0
TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:19925 (19.4 KB)  TX bytes:6293 (6.1 KB)
Interrupt:17 

eth0:avahi 
Link encap:Ethernet  
HWaddr 00:25:b3:7d:##:##  
inet addr:169.254.#.##  Bcast:169.254.255.255  Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
Interrupt:17 

lo
Link encap:Local Loopback  
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:2037 errors:0 dropped:0 overruns:0 frame:0
TX packets:2037 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:102040 (99.6 KB)  TX bytes:102040 (99.6 KB)

=========== ethtool results ======================
Supported ports: [ TP ]
Supported link modes:   10baseT/Half 10baseT/Full
	                100baseT/Half 100baseT/Full
	                1000baseT/Half 1000baseT/Full
Supports auto-negotiation: Yes
Advertised link modes:  10baseT/Half 10baseT/Full 
	                100baseT/Half 100baseT/Full 
	                1000baseT/Half 1000baseT/Full 
Advertised auto-negotiation: Yes
Speed: 100Mb/s
Duplex: Full
Port: Twisted Pair
PHYAD: 0
Transceiver: internal
Auto-negotiation: on
Supports Wake-on: pg
Wake-on: d
Current message level: 0x000000ff (255)
	Link detected: yes
```

---

### Post by Iowan on 2010-03-10
The **avahi** address means the machine failed to get a "normal" DHCP address - the fun begins... ;)

---

### Post by chili555 on 2010-03-10
You do have an ethernet interface, indicating a driver and your card have attached. Also, according to *ethtool*, your card has detected a link to the router, switch or other access point.> Link detected: yesSince you are running an older version of Ubuntu, you may be able to connect without regard to Network Manager. Please try:```
sudo /etc/init.d/NetworkManager stop
sudo dhclient eth0
```On some systems, the service is known as network-manager, so try both if the first command ends in an error.

Are you somehow required to use the same IP address as Windows? A static IP address, perhaps?

If *dhclient* times out, please post:```
dmesg | grep eth
```Thanks.

---

### Post by ClarkePeters on 2010-03-11
I tried the network manager and for some strange reason when I copied it over (which I do to prevent typos) yet it gave me "atop" instead of "stop", so of course it didn't work. I'm at home now and just caught the mistake. Nevertheless, I did go to the directory /etc/init.d and there was no NetworkManager or network-manager file or folder.

Then I did:
```

me@me-laptop:/etc/init.d$ sudo dhclient eth0
...
Listening on LPF/eth0/00:25:b3:7d:##:##
Sending on   LPF/eth0/00:25:b3:7d:##:##
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

me@me-laptop:/etc/init.d$ dmesg | grep eth
[   13.482127] Driver 'sd' needs updating - please use bus_type methods
[   13.482249]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   21.992040] sky2 eth0: addr 00:25:b3:7d:##:##
[   22.733269] sky2 eth0: enabling interface
[   24.564754] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   39.644630] eth0: no IPv6 routers present

```

when I did the above, enable roaming was off and I had my configuration in Network as "Automatic configuration (DHCP)".

I'll try the network manager again when I get back to work, but maybe the info above will help.

---

