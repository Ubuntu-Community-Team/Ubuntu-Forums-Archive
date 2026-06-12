---
title: "[wireless] Connected but no ping for a while"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by DBarzo on 2009-04-26
Hi, 

My system is:

- Acer TravelMate 5720
- Ubuntu 9.04

description: Wireless interface
product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:04:00.0
logical name: wmaster0
version: 61
serial: 00:1f:3b:4f:72:5f
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=iwlagn ip=192.168.1.4 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

I'm using Wicd.

Until yesterday I used hardy, and I have no problems. Today I upgraded to Jaunty and, on startup, the connection seems to be established (wicd says CONNECTED) but if I ping my router I get "Destination Host Unreachable".

This for the first 1 minutes...then the connection start to works!!
How can cause this issue?

PS. I've added a restart network on startup (/etc/init.d/networking restart) but it not solve..


Here some logs..

```

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.4 icmp_seq=3 Destination Host Unreachable
From 192.168.1.4 icmp_seq=5 Destination Host Unreachable
From 192.168.1.4 icmp_seq=6 Destination Host Unreachable
From 192.168.1.4 icmp_seq=8 Destination Host Unreachable
From 192.168.1.4 icmp_seq=9 Destination Host Unreachable
From 192.168.1.4 icmp_seq=13 Destination Host Unreachable
From 192.168.1.4 icmp_seq=15 Destination Host Unreachable
..... ..... ....
From 192.168.1.4 icmp_seq=48 Destination Host Unreachable
From 192.168.1.4 icmp_seq=49 Destination Host Unreachable
From 192.168.1.4 icmp_seq=50 Destination Host Unreachable
64 bytes from 192.168.1.1: icmp_seq=51 ttl=64 time=5.65 ms
64 bytes from 192.168.1.1: icmp_seq=52 ttl=64 time=1.11 ms
64 bytes from 192.168.1.1: icmp_seq=53 ttl=64 time=1.13 ms
64 bytes from 192.168.1.1: icmp_seq=54 ttl=64 time=1.07 ms
64 bytes from 192.168.1.1: icmp_seq=55 ttl=64 time=1.09 ms

``````

2009/04/25 20:36:21 :: ---------------------------
2009/04/25 20:36:21 :: wicd initializing...
2009/04/25 20:36:21 :: ---------------------------
2009/04/25 20:36:21 :: Automatically detected wireless interface wlan0
2009/04/25 20:36:21 :: found wireless_interface in configuration wlan0
2009/04/25 20:36:21 :: setting wireless interface wlan0
2009/04/25 20:36:21 :: automatically detected wired interface eth0
2009/04/25 20:36:21 :: found wired_interface in configuration eth0
2009/04/25 20:36:21 :: setting wired interface eth0
2009/04/25 20:36:21 :: found wpa_driver in configuration wext
2009/04/25 20:36:21 :: setting wpa driver wext
2009/04/25 20:36:21 :: found always_show_wired_interface in configuration False
2009/04/25 20:36:21 :: found use_global_dns in configuration False
2009/04/25 20:36:21 :: setting use global dns to False
2009/04/25 20:36:21 :: setting use global dns to boolean False
2009/04/25 20:36:21 :: found global_dns_1 in configuration None
2009/04/25 20:36:21 :: found global_dns_2 in configuration None
2009/04/25 20:36:21 :: found global_dns_3 in configuration None
2009/04/25 20:36:21 :: setting global dns
2009/04/25 20:36:21 :: global dns servers are None None None
2009/04/25 20:36:21 :: found auto_reconnect in configuration True
2009/04/25 20:36:21 :: setting automatically reconnect when connection drops
2009/04/25 20:36:21 :: found debug_mode in configuration 1
2009/04/25 20:36:21 :: found wired_connect_mode in configuration 1
2009/04/25 20:36:21 :: found signal_display_type in configuration 0
2009/04/25 20:36:21 :: found dhcp_client in configuration 0
2009/04/25 20:36:21 :: Setting dhcp client to 0
2009/04/25 20:36:21 :: found link_detect_tool in configuration 0
2009/04/25 20:36:21 :: found flush_tool in configuration 0
2009/04/25 20:36:21 :: Wireless configuration file found...
2009/04/25 20:36:21 :: Wired configuration file found...
2009/04/25 20:36:21 :: chmoding configuration files 0600...
2009/04/25 20:36:21 :: chowning configuration files root:root...
2009/04/25 20:36:21 :: Using wired interface...eth0
2009/04/25 20:36:21 :: Using wireless interface...wlan0
2009/04/25 20:36:21 :: WARNING: No path found for resolvconf
2009/04/25 20:36:21 :: WARNING: No path found for resolvconf
2009/04/25 20:36:21 :: autoconnecting... wlan0
2009/04/25 20:36:21 :: scanning start
2009/04/25 20:36:21 :: ifconfig wlan0 up
2009/04/25 20:36:22 :: iwlist wlan0 scan
2009/04/25 20:36:23 :: scanning done
2009/04/25 20:36:23 :: found 2 networks:
2009/04/25 20:36:23 :: 00:18:39:A4:B7:E9
2009/04/25 20:36:23 :: 00:1C:A2:80:85:7C
2009/04/25 20:36:23 :: ifconfig eth0 up
2009/04/25 20:36:25 :: No wired connection present, attempting to autoconnect to wireless network
2009/04/25 20:36:25 :: BarzoNET has profile
2009/04/25 20:36:25 :: trying to automatically connect to...BarzoNET
2009/04/25 20:36:25 :: Connecting to wireless network BarzoNET
2009/04/25 20:36:25 :: Putting interface down
2009/04/25 20:36:25 :: ifconfig wlan0 down
2009/04/25 20:36:25 :: Releasing DHCP leases...
2009/04/25 20:36:26 :: Setting false IP...
2009/04/25 20:36:26 :: ifconfig wlan0 0.0.0.0 
2009/04/25 20:36:26 :: ifconfig eth0 0.0.0.0 
2009/04/25 20:36:26 :: Stopping wpa_supplicant and any DHCP clients
2009/04/25 20:36:26 :: killall wpa_supplicant
2009/04/25 20:36:26 :: Flushing the routing table...
2009/04/25 20:36:26 :: ip route flush dev wlan0
2009/04/25 20:36:26 :: ip route flush dev eth0
2009/04/25 20:36:26 :: Generating psk...
2009/04/25 20:36:26 :: ['/usr/bin/wpa_passphrase', 'BarzoNET', '__MY_PASSHPHRASE_OMITTED__'']
2009/04/25 20:36:26 :: Attempting to authenticate...
2009/04/25 20:36:26 :: ['wpa_supplicant', '-B', '-i', 'wlan0', '-c', '/var/lib/wicd/configurations/001839a4b7e9', '-D', 'wext']
2009/04/25 20:36:26 :: Putting interface up...
2009/04/25 20:36:26 :: ifconfig wlan0 up
2009/04/25 20:36:26 :: iwconfig wlan0 mode managed
2009/04/25 20:36:26 :: ['iwconfig', 'wlan0', 'essid', 'BarzoNET', 'channel', '7', 'ap', '00:18:39:A4:B7:E9']
2009/04/25 20:36:26 :: WPA_CLI RESULT IS ASSOCIATED
2009/04/25 20:36:27 :: WPA_CLI RESULT IS 4WAY_HANDSHAKE
2009/04/25 20:36:28 :: WPA_CLI RESULT IS COMPLETED
2009/04/25 20:36:28 :: Setting static IP : 192.168.1.4
2009/04/25 20:36:28 :: ifconfig wlan0 192.168.1.4 netmask 255.255.255.0 
2009/04/25 20:36:28 :: Setting default gateway : 192.168.1.1
2009/04/25 20:36:28 :: route add default gw 192.168.1.1 dev wlan0
2009/04/25 20:36:28 :: Setting DNS : 192.168.1.1
2009/04/25 20:36:28 :: Connecting thread exiting.
2009/04/25 20:36:28 :: ifconfig wlan0
2009/04/25 20:36:28 :: IP Address is: 192.168.1.4

```Thanks,
Daniele.

---

### Post by DBarzo on 2009-05-01
Nobody can suggest me how to debug this situation or which component of the connection process I have to watch?

Thanks!
Daniele.

---

### Post by emnik on 2009-05-24
Hi I have exactly the same problem with xubuntu 9.04, although in my case the delay is usually more than 1 minute... Have you come to a solution?

---

### Post by DBarzo on 2009-05-24
Hi emnik!

 Unfortunately I have not found a solution yet!
I've also open an issue on launchpad but anyone have ansered me! 
([https://bugs.launchpad.net/ubuntu/+bug/367340](https://bugs.launchpad.net/ubuntu/+bug/367340))

I've also noted that this 'problem' is not related to the startup time, but the first time you attempt to use the connection: for example if you boot and don't use the connection (no ping, no open browser, and so on) for 10 minutes, and then you open a shell and make a ping you have the problem...

Also this issue maybe related to ipv6 support that in the new kernels is activated by default..

I hope that someone suggest us how to solve this!

Cheers,
Daniele.

---

### Post by stickyman on 2009-05-24
beginners question what is a ping and how does it work I gert kicked off some games because my ping rate is to high,how do I adjust it?

---

### Post by emnik on 2009-05-24
DBarzo thanks for the quick reply...

I also think it may be an ipv6 problem... maybe I'll try with an older kernel (lets say one from ubuntu 8.10 :-) But that would be on the end of the week. I'll get back to you...

---

### Post by DBarzo on 2009-05-27
> **emnik said:**
> DBarzo thanks for the quick reply...

I also think it may be an ipv6 problem... maybe I'll try with an older kernel (lets say one from ubuntu 8.10 :-) But that would be on the end of the week. I'll get back to you...

I have not found a solution / cause yet..
 I traced the connection with wireshark and the results:


```

    No.     Time        Source                Destination           Protocol Info
      1 0.000000    IntelCor_4f:72:5f     Broadcast             ARP      Who has 192.168.1.1?  Tell 192.168.1.4
      2 0.327556   192.168.1.2             192.168.1.255  BROWSER Domain/Workgroup Announcement EUROCOM, NT Workstation, Domain Enum
      3 0.999907    IntelCor_4f:72:5f     Broadcast             ARP      Who has 192.168.1.1?  Tell 192.168.1.4
      4 2.001247    IntelCor_4f:72:5f     Broadcast             ARP      Who has 192.168.1.1?  Tell 192.168.1.4
      5 3.011898    IntelCor_4f:72:5f     Broadcast             ARP      Who has 192.168.1.1?  Tell 192.168.1.4
      6 4.007926    IntelCor_4f:72:5f     Broadcast             ARP      Who has 192.168.1.1?  Tell 192.168.1.4
....
....
     65 61.312136   IntelCor_4f:72:5f     Broadcast             ARP      Who has 192.168.1.1?  Tell 192.168.1.4
     66 62.312150   IntelCor_4f:72:5f     Broadcast             ARP      Who has 192.168.1.1?  Tell 192.168.1.4
     67 63.327908   IntelCor_4f:72:5f     Broadcast             ARP      Who has 192.168.1.1?  Tell 192.168.1.4
     68 63.330395   Cisco-Li_a4:b7:e8     IntelCor_4f:72:5f     ARP      192.168.1.1 is at 00:18:39:a4:b7:e8
     69 63.330663   192.168.1.4           192.168.1.1           ICMP     Echo (ping) request
     70 63.330399   Cisco-Li_a4:b7:e8     IntelCor_4f:72:5f     ARP      192.168.1.1 is at 00:18:39:a4:b7:e8
     71 63.330404   Cisco-Li_a4:b7:e8     IntelCor_4f:72:5f     ARP      192.168.1.1 is at 00:18:39:a4:b7:e8
     72 63.330408   Cisco-Li_a4:b7:e8     IntelCor_4f:72:5f     ARP      192.168.1.1 is at 00:18:39:a4:b7:e8

``` The issue may depends by my router.... It is a linksys WAG325N
What kind of router you have?


Cheers,
Daniele.

---

### Post by Sevmpe on 2009-05-27
I have the same problem. After a period of network inactivity, it seems that the connection can't find the DNS to resolve any addresses although the connection appears to be fine. Actually, I can connect to other computers on the local network using their IP address without any problems. If I type ```
route
``` in a terminal, I get a full working connection again (e.g. ping working for [www.google.com](www.google.com)).

The problem appears both with network manager and wicd and my router is a Zyxel P660HW-D1 (a common model in Spain issued by Telefónica).

---

### Post by Mars73 on 2009-05-27
> **Sevmpe said:**
> I have the same problem. After a period of network inactivity, it seems that the connection can't find the DNS to resolve any addresses although the connection appears to be fine. Actually, I can connect to other computers on the local network using their IP address without any problems. If I type ```
route
``` in a terminal, I get a full working connection again (e.g. ping working for [www.google.com](www.google.com)).

The problem appears both with network manager and wicd and my router is a Zyxel P660HW-D1 (a common model in Spain issued by Telefónica).

Exact same problem here.
I tried a lot of things and thought I had nailed it but it keeps coming back.
Connection strenght and speed is good but sometimes out of nowhere it looses connection and some time later it comes back. Sometimes it stays on for only a few minutes, sometimes an hour.
Quite irritating if you watch streaming movies which usually are longer then a few minutes.
I've also activated backports and installed a newer kernel but problem is the same. Both with NM and WICD.
Belkin wireless G USB networkadapter attached to desktop PC with Ubuntu 9.04 and Belkin Pre-N router.
My laptop (with Ubuntu 9.04 as well) and intel wireless 3945abg works fine so I'm not suspecting my router.
Hope this get worked out quick.

---

### Post by jonobr on 2009-05-27
After upgrading to 9.04 I found Network manager to be a weeeee bit funky.

I saw the same problems you guys saw, so
I changed my ethernet settings to be unmanaged and static.
I configured my own resolv.conf, hosts file etc...as well as 
nm-system-settings.conf in /etc/NetworkManager and have not looked back.


I dont know if this will work for you all, but Im happier now.....

Good luck.....

---

### Post by emnik on 2009-05-28
I have a Linksys WAG200G Wireless router and I 'm using static IP's far my local network... and i don't think it's the router as with the same pci wireless card and the same route, on a different pc (different motherboard) I had no such problem for years!

---

### Post by emnik on 2009-06-08
The problem seem's to be the encryption method! If I choose no encryption or WEP everything works just fine! But for WPA... the usual problem. In the past WPA worked but I had compiled it from sources. In Ubuntu 9.04 WPA_supplicant is tighted up to the whole system and I couldn't uninstall it. What I tried without success was to compile WPA from sources and manual overwrite the binaries but the problem remains... SO FOR NOW THE SOLUTION IS WEP. I know it is not secure but I did everything I could think. I disabled wireless administration at the router, enables MAC adrress filter list for wireless access, disabled DHCP, RIP, ... and any other suggestion that could provide some more security is welcome!

---

### Post by Sevmpe on 2009-06-08
emnik,

I am using WEP, so I don't think the problem is the encryption method.

---

### Post by emnik on 2009-06-08
[Sevmpe]("http://ubuntuforums.org/member.php?u=86172") the only other thing I did was a bios update...

---

### Post by DBarzo on 2009-06-27
I've contact the Linksys support and they suggested me to upgrade the firmware to the latest version (for my router is 01.00.12) and to configure the router with these settings in the "Advanced Wireless settings":

Beacon Interval to 50
Fragmentation Threshold to 2304.
RTS Threshold to 2304 

This seems to have solved the problem!

---

### Post by copycat on 2009-09-28
> **DBarzo said:**
> I've contact the Linksys support and they suggested me to upgrade the firmware to the latest version (for my router is 01.00.12) and to configure the router with these settings in the "Advanced Wireless settings":

Beacon Interval to 50
Fragmentation Threshold to 2304.
RTS Threshold to 2304 

This seems to have solved the problem!

Let's hope it works... I have the same router and the same issues.  On other WPA encrypted routers my client connects without any problem. I wouldn't suggest to go to 01.00.12. This brought a lot of other issues to my router.(disconnecting ppoe, hanging weekly)  So I downgraded to 01.00.11. This was more stable.

---

### Post by copycat on 2009-09-29
> **copycat said:**
> Let's hope it works... I have the same router and the same issues.  On other WPA encrypted routers my client connects without any problem. I wouldn't suggest to go to 01.00.12. This brought a lot of other issues to my router.(disconnecting ppoe, hanging weekly)  So I downgraded to 01.00.11. This was more stable.

Didn't work for me... Contacted Linksys to check it for my WAG325N

---

### Post by copycat on 2009-10-02
I got a strange phonecall this morning from Linksys.
A nice person on the phone told me he was from Linksys support.  He wanted to let me know that <b>Linux clients are NOT supported on Linksys routers!</b>
I told him there modems are running Linux.  He was very sorry but it was the truth.  Does this mean that we can not use Linksys anymore... strange.... Just like this?  

I think Linksys is going to loose customers when they keep talking like this.

---

