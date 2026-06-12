---
title: "Newbie establishing wireless connection-Linksys"
date: 2006-01-31
forum: Networking &amp; Wireless
---

### Post by Quickbeam of Fangorn on 2006-01-31
New computer non propitatory. New user to Linux. Trying to establish wireless connection in home. 
Wireless card is Linksys WMP54G.
Processor - AMD 64 3500+.
Breezy Badger 5.10

Older computer is a gateway -windows XP currently connected to broadband provider via a Linksys router model WRG54T. 

I ran ~$ ifconfig

> eth1    Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: fe80::213:3d3ff:fe61:9ab0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          Interrupt:23 Base address:0x8000 

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:803 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          

Sudo iwlist eth1 scan
> Interface doesn't support scanning

route -n

Gateway reads 10.10.1.1 UG

#1) How do I establish my computer as the client (I'm assuming I have to run my wireless through the older computer then to the router) or can I run both computers directly to the router?

Thanks,

QB

---

### Post by spd106 on 2006-01-31
You should be able to connect straight through the router to the internet. I suggest you access the routers configuration page through the XP machine and make sure it's set as DHCP server.

Next configure your wireless card through the network-admin gui. Here all you need to do is make sure the card is set to DHCP and activated.

If you want to use the terminal, then try **man iwconfig**

There are several wifi guides in the [wiki]("https://wiki.ubuntu.com/WiFiHowto")

---

### Post by Quickbeam of Fangorn on 2006-01-31
I can't tell if it no recognizing the device, or the drive or the router or what?

Performed the following commands

sudo lshw -businfo

pci@01:08:0 ra0 network Ralink RT2500 802.11 

lspci -v

subsystem:Linksys:unknown device 0032
Flags:bus master, slow devsel, latency 32,
Capabilities: <available only to root> IRQ 18

sudo lspci -n

0000:01:08.0 0280:1814:0201 (rev 01)

sudo iwconfig

lo     no wireless
etho no wireless
ra0 RT2500 ESSID:"Linksys"
Mode - Managed "Frequency- 2.437 GHZ" Access Point- 00:12:17:28:6B:44
Bit Rate 54 MB/s Tx Power-18 dbm 
Encryption Key: off
Link Quality= 72/100 Signal level-44 dBm Noise level -193
Rx invalid nwid:0 RX invalid crypt:0 Rx invalid frag:0

sudo ifconfig

Rx packets:286
Tx packets:438
Collisions: 15

sudo dhclient

sito:unknown hardware address type 776
listening on LPF/ra0/00:12:17:82:78:03
Sending on same
Sending on Socket/fallback
DHCP DISCOVER on ra0 to 255.255.255.2555 port 67 interval 6


Any help/ideas?

---

### Post by Quickbeam of Fangorn on 2006-02-01
Is there any other commands I need to try to provide someone who may be able to provide me with some help here.

Thanks.

---

