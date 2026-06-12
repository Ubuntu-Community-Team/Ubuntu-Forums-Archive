---
title: "Ubuntu 8.10 connects to some wireless networks but not to others"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by prometheus1981 on 2009-03-28
Hello,
I have an old Dell PC that I did not use any more and I wanted to give it a second life. I have recently installed a brand new Asus WL-138G v2 wireless  PCI card and connected the PC to my LAN to update the OS and download the drivers for the card. The first day I was able to connect to my wireless WPA network and surf the web for a good couple of hours. The next day I booted up the PC and it stopped connecting to my WPA. I have not changed any settings on my PC or my router. I have rebooted several times and nothing! I have to neighbors who have unsecured wireless networks, and I was able to connect to neighbor 1 at that time. Since then I sometimes can connect to neighbor 1 wireless with 30% signal, I cannot connect to my wireless network with 60% signal. So far I yet have not had any problems with neighbor 2 wireless network with 37% signal, but I do not know how long before I start having problems connecting to that one as well. Please help!

PC: Dell Dimension 4550 Desktop
Card: Asus WL-138G v2 PCI card.
Chipset: Broadcom Corporation BCM4318 [AirForce One 54g]
OS: Ubuntu 8.10
Wireless encryption: WPA2
Kernel: 2.6.27-11-generic i686

Results from "lspci -v | less":
```
02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Device 100f
        Flags: bus master, fast devsel, latency 64, IRQ 21
        Memory at fe1fe000 (32-bit, non-prefetchable) [size=8K]
        Kernel driver in use: ndiswrapper
        Kernel modules: ssb

```

ifconfig:
```
wlan0     Link encap:Ethernet  HWaddr 00:24:8c:24:c3:bb  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:8cff:fe24:c3bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46991 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37431599 (37.4 MB)  TX bytes:4879474 (4.8 MB)
          Interrupt:21 Memory:fe1fe000-fe200000 
```

iwconfig (neighbor 2):
```
wlan0     IEEE 802.11g  ESSID:"the wasteland"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:10:FC:E7:33   
          Bit Rate=2 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

dmesg | grep "wlan0":
```
[   16.240554] wlan0: ethernet device 00:24:8c:24:c3:bb using NDIS driver: bcmwl5, version: 0x3644000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[   16.240595] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   35.093206] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  106.236874] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  117.012018] wlan0: no IPv6 routers present
[41134.996019] wlan0: no IPv6 routers present

```

sudo lshw -C network:
```
  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:24:8c:24:c3:bb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+ASUS,02/11/2005, 3.100.64.0 ip=192.168.1.109 latency=64 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:07:e9:7b:75:bb
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 02:8e:ea:0a:7d:c6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

lshw scan:
```
wlan0     Scan completed :
          Cell 01 - Address: 00:18:F8:C3:0B:D5
                    ESSID:"brundlenet"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:24:56:62:CA:D1
                    ESSID:"2WIRE606"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:13:10:05:49:7F
                    ESSID:"elaine"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:18:39:EF:81:B0
                    ESSID:"GaspyLan"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:22:3F:31:66:16
                    ESSID:"rivergate"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 00:30:BD:FB:B3:97
                    ESSID:"belkin54g"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:28/100  Signal level:-78 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 07 - Address: 00:13:10:FC:E7:33
                    ESSID:"the wasteland"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


```

Network Restart:
```
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]
```

Let me know if anyone needs any more information of my configuration :P

---

### Post by prometheus1981 on 2009-03-30
Any help on this will be very appreciated. Thanks.

---

### Post by Jota37 on 2010-08-27
I am having the same annoying problem with Ubuntu NBR 10.04 (on an Asus Eee 1000HE). 

It connects quickly and perfectly to my network at home (a protected WiFi network).

At work (unprotected WiFi), it used to connect fine until last Thursday -- this week it won't connect anymore (in between, there were software updates! I tried restarting using an older kernel, but to no avail).

If I boot the laptop in WinXP, it connects fine to the work network. Reboot in Ubuntu, it sometimes won't even SEE the network. If it does see it, it never connects.

Trying command line commands has gone up to the point where this shows up:

```

$ sudo dhclient wlan0
...
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Very annoying. Why is WinXP connecting beautifully and Ubuntu is failing miserably?

---

