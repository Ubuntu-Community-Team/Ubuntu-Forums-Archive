---
title: "ASUS PCE-N13 wireless card not working"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by rjg_munga on 2010-11-27
I need some help getting my wireless card working.
I have a ASUS PCE-N13 and I'm running ubuntu 10.10 AMD64.
I have confirmed that the card works running under win xp.

The problem I have is that it can't see any available networks.
I have downloaded and compile the latest driver from ASUS rt2860sta 2.1.0.0 and added these lines to the blacklist file.
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb

/etc/modprobe.d/blacklist.conf

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 20:cf:30:00:81:18  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::22cf:30ff:fe00:8118/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5807 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6348 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3631570 (3.6 MB)  TX bytes:976200 (976.2 KB)
          Interrupt:45 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16673 (16.6 KB)  TX bytes:16673 (16.6 KB)

wlan0     Link encap:Ethernet  HWaddr 70:71:bc:36:7f:86  
          inet6 addr: fe80::7271:bcff:fe36:7f86/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:630 (630.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

``````

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````

$ sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```Any ideas?
munga

---

### Post by rjg_munga on 2010-11-29
Bumping!!!
I could really do with some help guys.

---

