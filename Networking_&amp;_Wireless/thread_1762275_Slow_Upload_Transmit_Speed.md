---
title: "Slow Upload Transmit Speed"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by AMSlider on 2011-05-19
Hi all,

I hoping someone can help me with an issue I've been struggling with regarding the Realtek r8169 driver.  It seems that the onboard lan nic is somehow limited on the transmit on eth0 interface to anywhere from 30-90 KB/s.  The receive is usually around 10-30 MB/s.  

Here's some background that may be useful.  I recently upgraded my 10/100 Buffalo 4 port router to a Linksys e3000 10/100/1000 router running tomatousb.  I have a mix of windows and ubuntu machines on the network, most of which are wireless.  This machine is the my office hooked up to the router by 1 meter cat5 cabling.  I have tried many different cables, they all exhibit the same symptom.  In the posting below, I have temporarily added a usb wireless g nic to get some decent transmit speed.  I have tried the r6169 build (version 6.014) from [realtek]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=4&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8110SC%28L%29").  The 6.013 wouldn't compile.  I have also tried the 64 bit builds of windows 7 and vista inside of ndiswrapper.  They failed misably, but the XP 64 bit driver installed and actually gave me an IP address, though it wouldn't actually send any data, pings didn't work, etc.  

I've used netio to test network throughput between computers and bmon to realtime track it on the machine. 

Sorry for the long post.  Thanks for your time and help! 

Running Natty 64 bit

uname output:
```

# uname -a
Linux deeog 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

lspci -nn output:
```

# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82P965/G965 Memory Controller Hub [8086:29a0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82P965/G965 PCI Express Root Port [8086:29a1] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller [8086:2810] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller [8086:2820] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller [8086:2825] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G84 [GeForce 8600 GTS] [10de:0400] (rev a1)
[COLOR="Red"]02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet [10ec:8167] (rev 10)[/COLOR]
02:02.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]

```

ifconfig output:
```

# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:8d:9a:3c:1c  
          inet addr:192.168.2.44  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe9a:3c1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32874 (32.8 KB)  TX bytes:110579 (110.5 KB)
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:174220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:174220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99425062 (99.4 MB)  TX bytes:99425062 (99.4 MB)

rausb0    Link encap:Ethernet  HWaddr 00:12:17:76:5e:c4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9969 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9531 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8023901 (8.0 MB)  TX bytes:2403257 (2.4 MB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

lshw output:
```

# lshw -C Network
lspci -nn                 
  *-network        
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:50:8d:9a:3c:1c
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.44 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=1Gbit/s
       resources: irq:20 ioport:de00(size=256) memory:fdeff000-fdeff0ff memory:fdd00000-fdd1ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:3
       logical name: rausb0
       serial: 00:12:17:76:5e:c4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2500usb driverversion=2.6.38-8-generic firmware=N/A ip=192.168.2.4 link=yes multicast=yes wireless=IEEE 802.11bg

```

ethtool output:
```

# ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	                                     1000baseT/Half 1000baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes

```

Some say to remove ip6 to increase speed.  I used the following to no avail:
```

# ifconfig eth0 del fe80::250:8dff:fe9a:3c1c/64

```

This is where I'm throughly confused.  I've read many posts about the router/nic not properly communicating their capabilities and this is the typical reason for the slowness.  Firstly, I'd imagine the slowness would be in both directions, in this case it is only in the transmit side from the nic.  Anyways, I try to drop the speed to 100 and duplex to half, since that's all mii-diag says it the nic can do (lshw and ethtool (and Realtek) say it's gigabit capable).

```

# ethtool -s eth0 speed 100 duplex half autoneg off

# mii-diag -v 
mii-diag.c:v2.11 3/21/2005 Donald Becker (becker@scyld.com)
 http://www.scyld.com/diag/index.html
Using the default interface 'eth0'.
  Using the new SIOCGMIIPHY value on PHY 32 (BMCR 0x0000).
 Basic mode control register 0x2000: Auto-negotiation disabled, with
 Speed fixed at 100 mbps, half-duplex.
 You have link beat, and everything is working OK.
   This transceiver is capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, [COLOR="Red"]negotiation not complete[/COLOR].
 Your link partner is generating 100baseTx link beat  (no autonegotiation).
   End of basic transceiver information.

libmii.c:v2.11 2/28/2005  Donald Becker (becker@scyld.com)
 http://www.scyld.com/diag/index.html
 MII PHY #32 transceiver registers:
   2000 794d 001c c912 0de1 0080 000c 2001
   0000 0300 0000 0000 1007 f8a0 0000 3000
   0060 4c40 0000 6c42 1060 0000 700d 2108
   2740 8c00 0040 8062 846d 8000 0123 0000.
 Basic mode control register 0x2000: Auto-negotiation disabled!
   Speed fixed at 100 mbps, half-duplex.
 Basic mode status register 0x794d ... 794d.
   Link status: established.
   Capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation not complete.
 Vendor ID is 00:07:32:--:--:--, model 17 rev. 2.
   No specific information is known about this transceiver type.
 I'm advertising 0de1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT
   Advertising no additional info pages.
   IEEE 802.3 CSMA/CD protocol.
 Link partner capability is 0080: 100baseTx.
   [COLOR="Red"]Negotiation did not complete.[/COLOR]


# ethtool -s eth0 speed 100 duplex full autoneg off

# mii-diag -v 
mii-diag.c:v2.11 3/21/2005 Donald Becker (becker@scyld.com)
 http://www.scyld.com/diag/index.html
Using the default interface 'eth0'.
  Using the new SIOCGMIIPHY value on PHY 32 (BMCR 0x0000).
 Basic mode control register 0x2100: Auto-negotiation disabled, with
 Speed fixed at 100 mbps, full-duplex.
 You have link beat, and everything is working OK.
   This transceiver is capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation not complete.
 Your link partner is generating 100baseTx link beat  (no autonegotiation).
   End of basic transceiver information.

libmii.c:v2.11 2/28/2005  Donald Becker (becker@scyld.com)
 http://www.scyld.com/diag/index.html
 MII PHY #32 transceiver registers:
   2100 794d 001c c912 0de1 0080 000c 2001
   0000 0300 0000 0000 1007 f8a0 0000 3000
   0060 6c40 0000 2000 1060 0000 e00d 2108
   2740 8c00 0040 8062 846d 8000 0123 0000.
 Basic mode control register 0x2100: Auto-negotiation disabled!
   Speed fixed at 100 mbps, full-duplex.
 Basic mode status register 0x794d ... 794d.
   Link status: established.
   Capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation not complete.
 Vendor ID is 00:07:32:--:--:--, model 17 rev. 2.
   No specific information is known about this transceiver type.
 I'm advertising 0de1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT
   Advertising no additional info pages.
   IEEE 802.3 CSMA/CD protocol.
 Link partner capability is 0080: 100baseTx.
   [COLOR="Red"]Negotiation did not complete.[/COLOR]

# ethtool -s eth0 speed 1000 duplex half autoneg off
Cannot set new settings: Invalid argument
  not setting speed
  not setting duplex
  not setting autoneg

# ethtool -s eth0 speed 1000 duplex full autoneg off
Cannot set new settings: Invalid argument
  not setting speed
  not setting duplex
  not setting autoneg

# ethtool -s eth0 speed 1000 duplex full autoneg on

# mii-diag -v 
mii-diag.c:v2.11 3/21/2005 Donald Becker (becker@scyld.com)
 http://www.scyld.com/diag/index.html
Using the default interface 'eth0'.
  Using the new SIOCGMIIPHY value on PHY 32 (BMCR 0x0000).
 The autonegotiated capability is 01e0.
The autonegotiated media type is 100baseTx-FD.
 Basic mode control register 0x1000: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
   This transceiver is capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation complete.
 Your link partner advertised cde1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT, w/ 802.3X flow control.
   End of basic transceiver information.

libmii.c:v2.11 2/28/2005  Donald Becker (becker@scyld.com)
 http://www.scyld.com/diag/index.html
 MII PHY #32 transceiver registers:
   1000 796d 001c c912 0de1 cde1 000d 2001
   41f9 0300 3c00 0000 1007 f8a0 0000 3000
   0060 acc0 0000 6c42 1060 0000 100c 2108
   2740 8c00 0040 0106 097c 8000 0123 0000.
 Basic mode control register 0x1000: Auto-negotiation enabled.
 Basic mode status register 0x796d ... 796d.
   Link status: established.
   Capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation complete.
 Vendor ID is 00:07:32:--:--:--, model 17 rev. 2.
   No specific information is known about this transceiver type.
 I'm advertising 0de1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT
   Advertising no additional info pages.
   IEEE 802.3 CSMA/CD protocol.
 Link partner capability is cde1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   [COLOR="Blue"]Negotiation  completed.[/COLOR]

```

So why does "speed 1000 duplex full autoneg on" work, but it really isn't showing that speed?

Should I just install another nic?!

Thanks again!

---

### Post by dandnsmith on 2011-05-19
Just a thought - are you talking local net transfers, or internet upload?
In the UK, ADSL has a much more limited up transmission speed than down.
Can you check this on your router statistics, and see if the up sync is consistent with that rate?

---

### Post by AMSlider on 2011-05-19
> **dandnsmith said:**
> Just a thought - are you talking local net transfers, or internet upload?
In the UK, ADSL has a much more limited up transmission speed than down.
Can you check this on your router statistics, and see if the up sync is consistent with that rate?

Hey Derek, 

I'm sorry I should've posted that these are all internal LAN connections.  So the 30-90 KB/s is atrocious.

Thanks!

---

### Post by AMSlider on 2011-05-19
I've just tried the network out with a Natty 64-bit live cd and am still experiencing the same issue.  Any help would be most appreciated.

---

### Post by dandnsmith on 2011-05-20
It might be worth trying the NIC change - they're cheap enough.
But I really don't have a clue why this should happen - I've not experienced it.

---

### Post by AMSlider on 2011-05-20
I guess I'm going to pick one up today... it's a shame though.  I've even sent an email to Realtek support.  Of course, I haven't heard back...

Thanks for your time Derek.

---

### Post by AMSlider on 2011-05-26
I've now got an Intel Gigabit PCI-E card.  Works like a charm.  

FWIW, The Realtek support folks did email me, but nothing they suggested worked.  Kudos to them.

---

### Post by dandnsmith on 2011-05-26
Glad to hear you're sorted.

---

### Post by ahendriks on 2011-11-18
@AMSlider; your sollution is covered here: [http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)

I really don't understand why this isn't fixed already... As far as i know this problem persists for a few years now! (above tread started on December 27th 2008!)

---

