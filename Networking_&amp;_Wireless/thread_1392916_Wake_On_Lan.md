---
title: "Wake On Lan"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by Chrissd on 2010-01-28
Hi,

I'm trying to get Wake On Lan to work on this computer, but it's not working, and I'm not sure why. 

I've gone into bios, and turned it on.
ifconfig returns this:
```

eth0      Link encap:Ethernet  HWaddr 00:d0:09:cd:ls:9f  
          inet addr:192.168.1.75  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:9ff:fefb:ae1a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1788 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:922603 (922.6 KB)  TX bytes:852136 (852.1 KB)
          Interrupt:11 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```

In /etc/init.d/ I have a file called "wakeonlan" which has 
```

#!/bin/bash
ethtool -s eth0 wol g
exit

``` and I then "chmod a+x wakeonlanconfig" and added it via "update-rc.d -f wakeonlanconfig defaults"

Then sudo halt'd. No joy when trying to wake up. In other threads I've read about other things, so I'll put extra info here incase it's any use.

ethtool eth0
```
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pg
	Wake-on: g
	Current message level: 0x000000c5 (197)
	Link detected: yes

```
```

acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. PCI0	  S4	 disabled  no-bus:pci0000:00
  2. PS2M	  S4	 disabled  pnp:00:05
  3. PS2K	  S4	 disabled  pnp:00:06
  4. UAR1	  S4	 disabled  pnp:00:08
  5. UAR2	  S4	 disabled  pnp:00:09
  6. USB1	  S4	 disabled  pci:0000:00:02.2
  7. USB2	  S4	 disabled  pci:0000:00:02.3
  8. LAN	  S4	 disabled  pci:0000:00:03.0
  9. MDM	  S4	 disabled  
  10. AUD	  S4	 disabled  
  11. SLPB	  S4	*enabled   

```

Thank in advance! :D

---

