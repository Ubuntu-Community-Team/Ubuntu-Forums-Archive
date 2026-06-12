---
title: "Internet not working"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by Hex08 on 2010-06-29
I am fairly new to Linux and recently installed 10.04 on my laptop. Since doing so I am unable to connect to the internet either wirelessly or with a wired connection. I have gone through much of the troubleshooting I found on this site and have had no luck. My ethernet card is recognized by Ubuntu as is the built-in wireless card and the usb card I tried. My other computer connects just fine. 
 
I would appreciate any help. Thanks.

---

### Post by Zimmer on 2010-06-29
You did not give your laptop the same hostname as your 'other' computer by any chance?
What OS is the other computer using??

These steps for info may enlighten those who know better than I as to what might be the problem
1. Please post output of ifconfig eth0 (Depends on your interface number)
2. Please post output of lspci | grep Eth
3. Please post output of route -n

in a terminal you could try the commands:

sudo ifconfig eth0 up
sudo dhclient eth0

and see if that generates a conection for you..

---

### Post by Iowan on 2010-06-29
**ifconfig -a** should show IP info on all interfaces.
**sudo lshw -C network** should show more info on drivers, alias, etc.
If interface(s) has/have IP address(es), try pinging internet by IP address (74.125.95.147).

---

### Post by Hex08 on 2010-06-29
Zimmer,
I gave the laptop a different a different hostname. My other (two, actually) computers are running Windows Vista and 7.
 
I can't copy and paste the info you asked for so I will type it by hand and hope it is right.
ifconfig eth0:
Link encap:Ethernet HWaddr 00:0a:e4:dd:75:2f
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqeuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interupt:20 Base address: 0x3000
 
lspci | grep Eth:
06:07.0 Ethernet controller: Realtek Semiconductor Co. Ltd. RTL-8139/8139C/8139C+ (rev 10)
 
route -n (I assume there should be more info than what I am posting for this one since it looks as if these are column headers. I left nothing out.)
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
 
Iowan
Here is the result of what you had me try.
 
ifconfig -a:
eth0 
Link encap:Ethernet HWaddr 00:0a:e4:dd:75:2f
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqeuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interupt:20 Base address: 0x3000
 
eth0:avahi encap:Ethernet HWaddr 00:0a:e4:dd:75:2f
inet addr:169.254.8 41 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interupt:20 Base address:0x3000
 
lo
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:716 errors:0 dropped:0 overruns:0 frame:0
TX packets:716 errors:0 dropped:0 overruns: 0 carrier:0
collisions:0 txqueuelen:0
RX bytes:57216 (57.2 KB) TX bytes:57216 (0.0 B)
 
wlan0
Link encap:Ethernet HWaddr:00:14:a5:60:80:bb
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes: 0 (0.0 B) TX bytes:0 (0.0 B)
 
sudo lshw -C network
*-network:0
description: Network controller
product: BCM4318 [Airforce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id:5
bus info: pci@0000:06:05.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pcibridge latency=120
resources: irq20 memory:b0101fff
*-network:1
description: Ethernet interface
product: RTL-8139/839c/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id:7
bus info: pci@0000:06:07.0
logical name: eth0
version: 10
serial: 00:0a:e4:dd:75:2f
size10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
configuration: autonegotiatio=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
resources: irq20 ioport:3000(size=256) memory:b0103000-b01030ff
*-network DISABLED
escription: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:14:a5:60:80:bb
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
 
 
Thanks for the help.

---

### Post by Hex08 on 2010-06-30
Bumped in hope of some help.

---

### Post by Zimmer on 2010-06-30
By way of a quick reply ;)

[http://ubuntuforums.org/showthread.php?t=197102&highlight=4318&page=196](http://ubuntuforums.org/showthread.php?t=197102&highlight=4318&page=196)

[https://help.ubuntu.com/community/WifiDocs/Driver/b43](https://help.ubuntu.com/community/WifiDocs/Driver/b43)

[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

All have various help info (from various time periods ) for your Broadcom card.

My suggestion is to read all of them carefully and search the forums again for recent  Broadcom issues, with relevance to your version of Ubuntu.... and see what turns up and work out the way forward from there..

Regards
Zimmer

---

### Post by Hex08 on 2010-06-30
Problem fixed. Pretty easy, actually. I followed the instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43) - No Internet access.
 
Thanks for the help.

---

### Post by Zimmer on 2010-07-02
Glad to be of assistance.... ;)

---

