---
title: "can not see any wireless networks"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by bark01 on 2010-01-07
hi,

I have an acer revo and i'm trying to run xbmc live from boot. I can not however get the wireless card to pick up any networks. I can access the terminal session to interact with the ubuntu workings but i'm new to this and i'm stuck. I don't know of any way to transport the code from the terminal session to my laptop so i'll type out the relevant bits.

I have tried the following commands

**lspeci:**

the last entry relates to wireless

05:00.0 Ethernet controller: Atheros Communications inc. AR5001 wireless network adapter (rev 01)

**ifconfig**

lo link encap:local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: : : 1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 METRIC:1
RX packets: 48 errors:0 dropped:0 overruns:0 frame:0
TX packets: 48 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:15680 (15.6 kb) TX bytes:15680 (15.6 Kb)


wlan0 Link encap:Ethernet HWaddr 0c:60:76:68:5b:1a
UP BROADCAST MULTICAST MTU:1500 METRIC:1
RX packets: 0 errors:0 dropped:0 overruns:0 frame:0
TX packets: 0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0 kb) TX bytes:0 (0 Kb)

wmaster0 Linkl encap:UNSPEC HWaddr 0c-60-76-68-5b-1a-00-00-00-00-00-00-00-00-00-00
UP RUNNING MTU:0 METRIC:1
RX packets: 0 errors:0 dropped:0 overruns:0 frame:0
TX packets: 0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0 kb) TX bytes:0 (0 Kb)

**iwconfig**

lo no wireless extensions
eth0 no wireless extensions
wmaster0 no wireless extensions
wlan0 IEEE 802.11bg ESSID:""
Mode:Managed Frequency:2.412 GHz Acess Point: Not Associated
TX-Power=20 dBm
retry Long limit:7 RTS thrff Fragment thr: off
Power managment: off
all the rest of thevalues are set to 0


I have also tried 

**sudo dhclient wlan0**

listening on LPF/wlan0/0c:60:76:68::5b:1a
sending on LPF/wlan0/0c:60:76:68::5b:1a
sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS recived.
No working leases in persistent database - sleeping.


The router i'm using is a dlink dir-655, it doesn't have any protection on it and the network is a 802.11 n/g/b mix 2.437 ghz channel 6

anyone got any ideas?

---

