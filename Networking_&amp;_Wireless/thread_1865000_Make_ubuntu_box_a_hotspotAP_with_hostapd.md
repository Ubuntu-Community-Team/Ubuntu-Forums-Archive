---
title: "Make ubuntu box a hotspot/AP with hostapd"
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by vangop on 2011-10-19
Hi!
I'm trying to make an ubuntu 11.10 box a hotspot with hostapd.
I have a 
```
t$ lspci -vnn | grep 14e4
44:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```
I have carefully searched and followed all the info I could find.
1. Replaced Broadcom STA driver with b43 (as [described]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"))
2. installed and configured hostapd (as [described]("http://linuxwireless.org/en/users/Documentation/hostapd"))
at this point I should be able to connect the clients with statc ip settings.
Yes, the clients are connected ok, but instantly reconnected a few times and after that finally disconnected (android phone)
Win7 client says connecting.. taking to long to connect... disconnecting.
This is what the sysout is saying:
```
$ sudo hostapd ~/hostapd.conf
Configuration file: /home/akm/hostapd.conf
Using interface wlan0 with hwaddr 5c:ac:4c:1a:6a:91 and ssid 'badlands'
wlan0: STA 8c:77:12:77:40:27 IEEE 802.11: authenticated
wlan0: STA 8c:77:12:77:40:27 IEEE 802.11: associated (aid 1)
AP-STA-CONNECTED 8c:77:12:77:40:27
wlan0: STA 8c:77:12:77:40:27 RADIUS: starting accounting session 4E9F21DC-00000000
wlan0: STA 8c:77:12:77:40:27 IEEE 802.11: authenticated
wlan0: STA 8c:77:12:77:40:27 IEEE 802.11: associated (aid 1)
AP-STA-CONNECTED 8c:77:12:77:40:27
wlan0: STA 8c:77:12:77:40:27 RADIUS: starting accounting session 4E9F21DC-00000001

```

Nothing special.
This is the ifconfig
```
$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:b3:34:bb  
          inet addr:10.22.212.155  Bcast:10.22.213.255  Mask:255.255.254.0
          inet6 addr: fe80::8aae:1dff:feb3:34bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1241962 errors:0 dropped:0 overruns:0 frame:0
          TX packets:547577 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1132875747 (1.1 GB)  TX bytes:73083115 (73.0 MB)
          Interrupt:20 Memory:d7400000-d7420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1562 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:158891 (158.8 KB)  TX bytes:158891 (158.8 KB)

mon.wlan0 Link encap:UNSPEC  HWaddr 5C-AC-4C-1A-6A-91-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7470 (7.4 KB)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:94.27.66.46  P-t-P:94.27.127.8  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:1109503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:472629 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:893760676 (893.7 MB)  TX bytes:37070779 (37.0 MB)

wlan0     Link encap:Ethernet  HWaddr 5c:ac:4c:1a:6a:91  
          inet addr:192.168.99.49  Bcast:192.168.99.255  Mask:255.255.255.0
          inet6 addr: fe80::5eac:4cff:fe1a:6a91/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3372 errors:0 dropped:0 overruns:0 frame:0
          TX packets:539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:257136 (257.1 KB)  TX bytes:99801 (99.8 KB)

```

and finally the hostapd config. I have even disabled security.
```
interface=wlan0
driver=nl80211
ssid=badlands
channel=8
hw_mode=g

```

I have a network manager, but since the wlan0 is static specified in /etc/network/interfaces it says that wireless device is not managed. So it is not interfering. Also tried to stop network-manager service, but it didn't help.
Can you plz share your thoughts?

---

### Post by vangop on 2011-10-20
I've posted to the hostapd list if no one will reply here...

---

### Post by collisionystm on 2011-10-20
I made my laptop an AD-HOC hot spot once. Installed dhcp3-server, created a wireless network, and when people connected they got the IP.

---

### Post by vangop on 2011-10-21
That's not really giving me a hint :)
I got a reply from hostap guys saying that hostap logs look fine and I need to debug clients/driver..
Anybody can help me?

---

### Post by igor.ibit on 2011-11-12
im having a similar issue with ath5k.

I set hostapd with minimal settings as described above.

when i use another Ubuntu comp to connect to the AP comp i get the following:
```
wlan0: STA 00:1d:0f:b4:d7:7a IEEE 802.11: authenticated
wlan0: STA 00:1d:0f:b4:d7:7a IEEE 802.11: associated (aid 2)
AP-STA-CONNECTED 00:1d:0f:b4:d7:7a
wlan0: STA 00:1d:0f:b4:d7:7a RADIUS: starting accounting session 4EBEB183-00000008
AP-STA-DISCONNECTED 00:1d:0f:b4:d7:7a

```and its just repeats itself without any connection.

conf file:
```
interface=wlan0
driver=nl80211
ssid=igor
#
hw_mode=g
channel=4
max_num_sta=15
```iwconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:6f:35:bb  
          inet addr:132.72.110.78  Bcast:132.72.110.127  Mask:255.255.255.128
          inet6 addr: fe80::21c:c0ff:fe6f:35bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8073557 (8.0 MB)  TX bytes:2564028 (2.5 MB)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

mon.wlan0 Link encap:UNSPEC  HWaddr 00-1D-0F-B4-D7-76-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1000 (1000.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:0f:b4:d7:76  
          inet6 addr: fe80::21d:fff:feb4:d776/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:179530 (179.5 KB)  TX bytes:226927 (226.9 KB)

```
any suggestions on what im doing wrong so far?

---

