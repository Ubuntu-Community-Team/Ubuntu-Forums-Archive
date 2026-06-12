---
title: "can't view wireless network (nor connect)"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by jdripper on 2009-09-15
I'm new to ubuntu, having mostly used gentoo in the past, I though I would give this a try.

I have installed Ubuntu on a Toshiba Tecra M10 version:
Description:    Ubuntu 8.04.3 LTS
Release:    8.04
Codename:    hardy

The wireless hardware seems to be OK:
```
id:    network
description:     Wireless interface
product:     Intel Corporation
vendor:     Intel Corporation
physical id:     
0
bus info:     
pci@0000:02:00.0
logical name:     
wmaster0
version:     00
serial:     XXXXXXXXX
width:     64 bits
clock:     33MHz
capabilities:     pm msi pciexpress bus_master cap_list logical ethernet physical wireless
configuration:    
broadcast    =    yes
driver    =    iwlagn
latency    =    0
module    =    iwlagn
multicast    =    yes
wireless    =    IEEE 802.11abgn
``````
~# lsmod | grep iwlagn
iwlagn                148100  0 
iwlcore               162500  1 iwlagn
iwlwif5k_mac80211     243316  2 iwlagn,iwlcore
iwlwifi5k_cfg80211     33504  3 iwlagn,iwlcore,iwlwif5k_mac80211


```"iwlist wlan0 scan" shows several wireless networks, but not mine.

I cannot connect to my network by using the network applet on the panel, or "wifi rader"  nor via the command line with "iwconfig".
It simply prompts for the encryption key again and again.
I'm sure it's the right key, I have other wireless devices.
Interestingly I cannot connect to an unsecured wireless network either.

It never gets associated to an access point :
```
:~# iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"giveuswires"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:XXXXXXXXXXXXXXXXXXXXX
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```Will Ubuntu automatically switch the card through 802.11 a/b/g/n ?
Any ideas on what I might be missing here ?

I'm dual booting with XP and it connects to the wireless net just fine.

---

### Post by jdripper on 2009-09-15
No ideas at all, anyone ?

---

### Post by Iowan on 2009-09-15
Network applet? You installed desktop? Does it have Network Manager (is that the applet)? Check if the interface is configured in */etc/network/interfaces*.

---

### Post by uylug on 2009-09-15
Run this and see if you get a wireless connection

```
sudo dhclient wlan0
```

```

ping google.com
```

---

### Post by jdripper on 2009-09-16
[@Iowan]("http://swiss.ubuntuforums.org/member.php?u=65323")

Yes, Network manager is what I meant.

```

~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


:~$ ifconfig -a


eth0      Link encap:Ethernet  HWaddr XXXXXXXXXXXXXX  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: xxxxxxxxxxxxxxxx:6341/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40427 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:44345522 (42.2 MB)  TX bytes:6719483 (6.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1485 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1485 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84116 (82.1 KB)  TX bytes:84116 (82.1 KB)

wlan0     Link encap:Ethernet  HWaddr XXXXXXXXXXXXXX  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr XXXXXXXXXXXXXXXXXXXXXXXXXX  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

eth0 is not in /etc/network/interfaces but that works perfectly.
I'll also note that the wlan0 interface is "up" when the machine has booted up.

As I mentioned "WiFI Rader" is able to display some wireless networks around me.
I would conclude from that that it the software WIFi Rader can interact with the hardware sufficiently to scan the airwaves for signals. The same for "iwlist wlan0 scan"

[@uylug]("http://swiss.ubuntuforums.org/member.php?u=894902")

I can't even associate with an access point, therefore it's useless to try and get an IP address.

---

### Post by jdripper on 2009-09-16
OK, updated /etc/network/interfaces :
```

# cat /etc/network/interfaces
auto lo wlan0
iface lo inet loopback
iface wlan0 inet dhcp
wireless-essid   giveuswires
wireless-key     xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
wireless-channel 6
wireless-mode    managed

```No joy still :
```

~# /etc/init.d/networking start
 * Configuring network interfaces... Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Input/output error.
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:22:fa:3b:a0:26
Sending on   LPF/wlan0/00:22:fa:3b:a0:26
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```At least now I have an error message :

**Error for wireless request "Set Frequency" (8B04) :**

**wmaster0: unknown hardware address type 801**

---

### Post by uylug on 2009-09-16
What is the output of :

[/code]sudo iwlist scan[/code]

---

### Post by jdripper on 2009-09-16
As previously indicated, iwlist wlan0 scan sees a bunch of other networks, just not mine:


```


wlan0     Scan completed :
          Cell 01 - Address: 00:16:CF:8C:4A:A7
                    ESSID:"Livebox-AD68"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/100  Signal level:-76 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000007cf898f857
                    Extra:Last beacon:1912ms ago
          Cell 02 - Address: 2A:ED:05:C3:16:50
                    ESSID:"pierreevelynec"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/100  Signal level:-77 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000010c2fc09268
                    Extra:Last beacon:1908ms ago
          Cell 03 - Address: 2E:EB:29:78:5C:10
                    ESSID:"Flop"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=80/100  Signal level:-54 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000023f3a6a830
                    Extra:Last beacon:1912ms ago
          Cell 04 - Address: 2E:EB:29:78:5C:12
                    ESSID:"FreeWifi"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=83/100  Signal level:-51 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000023f3a6e02f
                    Extra:Last beacon:1896ms ago
          Cell 05 - Address: 2E:EB:29:78:5C:13
                    ESSID:"freephonie"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=84/100  Signal level:-50 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000023f3a6e462
                    Extra:Last beacon:1896ms ago
          Cell 06 - Address: 2A:ED:05:C3:16:52
                    ESSID:"FreeWifi"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/100  Signal level:-77 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000010c2fc09a46
                    Extra:Last beacon:1904ms ago
          Cell 07 - Address: 2A:ED:05:C3:16:53
                    ESSID:"freephonie"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/100  Signal level:-77 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000010c2fc0aefb
                    Extra:Last beacon:1900ms ago
          Cell 08 - Address: 0A:1B:5D:F3:75:34
                    ESSID:"Maison"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/100  Signal level:-82 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000026b81bb5a33
                    Extra:Last beacon:1940ms ago
          Cell 09 - Address: 0A:1B:5D:F3:75:36
                    ESSID:"FreeWifi"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/100  Signal level:-83 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000026b81bce056
                    Extra:Last beacon:1836ms ago
          Cell 10 - Address: 0A:1B:5D:F3:75:37
                    ESSID:"freephonie"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/100  Signal level:-87 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000026b81bd1836
                    Extra:Last beacon:1824ms ago
          Cell 11 - Address: 2E:EB:29:78:5C:11
                    ESSID:""
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=80/100  Signal level:-54 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000023f3a6db3b
                    Extra:Last beacon:1900ms ago
          Cell 12 - Address: 56:42:11:A0:71:CE
                    ESSID:"FreeWifi"
                    Mode:Master
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=61/100  Signal level:-71 dBm  Noise level=-127 dBm
                    Encryption key:off
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:tsf=000000d84932838f
                    Extra:Last beacon:1844ms ago
          Cell 13 - Address: 56:42:11:A0:71:CF
                    ESSID:"freephonie"
                    Mode:Master
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=61/100  Signal level:-71 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:tsf=000000d849328cda
                    Extra:Last beacon:1844ms ago
          Cell 14 - Address: 00:1F:33:E0:01:0F
                    ESSID:"NUMERICABLE-0FA0"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/100  Signal level:-79 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000003ab88ba4005
                    Extra:Last beacon:1596ms ago
          Cell 15 - Address: 00:1A:2B:19:E1:03
                    ESSID:"NUMERICABLE-F395"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/100  Signal level:-78 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000021d6fe2c007
                    Extra:Last beacon:1632ms ago
          Cell 16 - Address: 00:1D:60:BD:18:06
                    ESSID:"NUMERICABLE-C6C0"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/100  Signal level:-85 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000004b047cbb008
                    Extra:Last beacon:1604ms ago
          Cell 17 - Address: 06:1D:6A:57:0B:5C
                    ESSID:"Livebox-caf1"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/100  Signal level:-71 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A4C1003FFFF000000000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000002bb5e5d0e7c
                    Extra:Last beacon:1700ms ago
          Cell 18 - Address: 06:1D:6A:56:F6:9E
                    ESSID:"Livebox-d799"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/100  Signal level:-83 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A4C1003FFFF000000000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000001f79fa74954
                    Extra:Last beacon:1692ms ago
          Cell 19 - Address: 00:90:D0:EC:78:61
                    ESSID:"SpeedTouch1DE222"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/100  Signal level:-80 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000193d8e0b753
                    Extra:Last beacon:1684ms ago
          Cell 20 - Address: 00:16:38:21:CD:8D
                    ESSID:""
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/100  Signal level:-71 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000898affa6c9
                    Extra:Last beacon:1652ms ago
          Cell 21 - Address: 00:17:33:28:2D:FD
                    ESSID:"NEUF_2DFC"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/100  Signal level:-73 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000dd54dfabaa
                    Extra:Last beacon:1524ms ago
          Cell 22 - Address: 00:17:33:28:2E:04
                    ESSID:"Neuf WiFi"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/100  Signal level:-74 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000dd54df9fd9
                    Extra:Last beacon:1528ms ago
          Cell 23 - Address: 00:17:33:34:21:1D
                    ESSID:"NEUF_211C"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/100  Signal level:-83 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000003ab837f3008
                    Extra:Last beacon:1504ms ago
          Cell 24 - Address: 2A:ED:05:C3:16:51
                    ESSID:""
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/100  Signal level:-77 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000010c2fc057bc
                    Extra:Last beacon:1924ms ago
          Cell 25 - Address: 62:F5:4E:91:0B:0E
                    ESSID:"FreeWifi"
                    Mode:Master
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=42/100  Signal level:-84 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000003ab8353d653
                    Extra:Last beacon:1640ms ago
          Cell 26 - Address: 00:17:33:ED:AD:01
                    ESSID:"mywifi"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=72/100  Signal level:-62 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000009aa3b48a46f
                    Extra:Last beacon:1496ms ago
          Cell 27 - Address: 00:17:33:ED:AD:08
                    ESSID:"Neuf WiFi FON"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=72/100  Signal level:-62 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000009aa3b48a094
                    Extra:Last beacon:1496ms ago
          Cell 28 - Address: 00:17:33:14:F9:08
                    ESSID:"Neuf WiFi FON"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/100  Signal level:-77 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000b5819cf300
                    Extra:Last beacon:1512ms ago
          Cell 29 - Address: 00:17:33:14:F9:01
                    ESSID:"NEUF_F900"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/100  Signal level:-76 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000b5819cf6db
                    Extra:Last beacon:1512ms ago
          Cell 30 - Address: 00:17:33:71:5E:0C
                    ESSID:"Neuf WiFi FON"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/100  Signal level:-80 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000a1ae40b4e1
                    Extra:Last beacon:1512ms ago
          Cell 31 - Address: 00:1D:19:58:F6:96
                    ESSID:"FOUCHER"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/100  Signal level:-86 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000032a5a02cc
                    Extra:Last beacon:1508ms ago
          Cell 32 - Address: 00:17:33:71:5E:05
                    ESSID:"NEUF_5E04"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/100  Signal level:-81 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000a1ae40b036
                    Extra:Last beacon:1512ms ago
          Cell 33 - Address: 00:17:33:34:21:24
                    ESSID:"Neuf WiFi"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/100  Signal level:-83 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000003ab837f34b3
                    Extra:Last beacon:1504ms ago
          Cell 34 - Address: 62:F5:4E:91:0B:0D
                    ESSID:""
                    Mode:Master
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=40/100  Signal level:-85 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000003ab8353df60
                    Extra:Last beacon:1636ms ago
          Cell 35 - Address: 00:19:15:3A:11:E8
                    ESSID:""
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/100  Signal level:-71 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000001ac3a91e6
                    Extra:Last beacon:1684ms ago



```

---

### Post by uylug on 2009-09-16
Okay, I got it.

Can you confirm this is not an issue related to your AP, ie AP not broadcasting name or something?

---

### Post by jdripper on 2009-09-17
AP is broadcasting the essid. I can connect to it with this same machine booted into windows.
I can also connect to it with various other decides, laptops, mobiles phones etc...

AP is working just fine, as mentioned it works with other devices.

---

### Post by jdripper on 2009-09-17
One thing that I initially said which may have been missed is that I can't connect to any of the visible networks. (yes, of course the unsecured ones )

---

### Post by louigi600 on 2009-09-17
On my 4965 AGN I need to first do 
ifconfig wlan0 up
then manually set the essid (or run wpa_supplicant)

It appears that the firmware network monitor is not working properly with the linux kernel driver ....

See if this gets you going

---

### Post by wilee-nilee on 2009-09-17
In the past I have had problems with network manager, and wifi radar has never worked for me, but wicd is a great replacement. If you can get on the web via a ether net plug you might consider trying out wicd it will install and remove network manger in one fell swoop. This is a consideration if the problem is actually in the network manager. 

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by jdripper on 2009-09-17
I booted in windows XP on the same machine and I can see that the wireless network is operating on a frequency of:  2.472GHz
In ubuntu it fails when trying to use this frequency :
```

:~# iwconfig wlan0 freq 2.472G
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Invalid argument.

```

The command was run as root, so pls don't tell me "you need to use sudo !"

Is there an updated driver for my hardware ?

---

### Post by jdripper on 2009-09-17
Tried wicd, I can connect to some of the other visible wifi networks, but still can't connect to me.

I would think it comes down to being able to get the right frequency. Any ideas on that ?

---

### Post by wilee-nilee on 2009-09-17
> **jdripper said:**
> Tried wicd, I can connect to some of the other visible wifi networks, but still can't connect to me.

I would think it comes down to being able to get the right frequency. Any ideas on that ?

I am not familiar with the frequency problem I have never heard of that, but that doesn't mean it isn't a valid problem. So you can see your network now with wicd? whereas you couldn't with the network manager. Have you just tried to reboot, that might get it working. Also on the wicd main page there are instructions to change a file I had to do this every time a few distros ago, I don't recall what Ubuntu your running.

---

### Post by jdripper on 2009-09-17
No, still can't see my network with wicd.

Can't see it with "iwlist wlan0 scan" so I won't see it with anything else. Network manager/wicd/wifi radar are just GUI front ends for what is essentially a iwlist scan

---

### Post by t0mppa on 2009-09-17
Well, 2.472 GHz is channel 13, whereas earlier you put into the interfaces file that your AP uses channel 6 (2.437 GHz). Also all the APs listed on your scan are on channels 1-11. Try running **iwlist wlan0 channels** and see how many channels it lists.

There are regional preferences for channels: in US, it is prohibited to use a channel above 11, but in Europe 12 & 13 can be used as well and in Japan there's also channel 14.

If you can only list 11 channels, it could be your system thinks you're in US and you have to manually force the domain to EU or JP ```
options cfg80211 ieee80211_regdom=EU
``` or ```
options lbm_cw_cfg80211 ieee80211_regdom=JP

```depending on which module is used by your current kernel (cfg80211 was renamed to lbm_cw_cfg80211 in latest kernels), in your */etc/modprobe.d/options* file. Naturally an alternative to this is simply editing your AP configuration and having it use a lower channel that is available even on US soil.

Also not being able to change the frequency sounds like a big problem, so it could simply be a driver issue. However, since I don't have an Intel chip myself, can't really give much advice on that field.

---

### Post by jdripper on 2009-09-17
"iwlist wlan0 channels" doesn't seems to be a valid command.[B]
iwlist wlan0 scan | grep Channel [/B]only shows channels 1 to 11 as you already suspected. 
Don't really see the module you mention, but I tried the next closest one :
```

~# lsmod | grep cfg802
iwlwifi5k_cfg80211     33504  3 iwlagn,iwlcore,iwlwif5k_mac80211
:~# 
:~# cat /etc/modprobe.d/options 
# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2
options iwlwifi5k_cfg80211 ieee80211_regdom=EU

```
I can still only see channels 1 to 11. (after reebot) .Setting my AP to channel 3 allows me to connect to it.

Though I want it to be able to use the European range. Any other ideas on how I can get that going ?

---

### Post by jdripper on 2009-09-17
A bit of googling turned this up as what should be added to /etc/modprobe.d/options

```

options cfg80211 ieee80211_regdom=EU

```Still no joy though.

I'm on :

:~# uname -r
2.6.24-24-generic

---

### Post by t0mppa on 2009-09-18
Sorry about the typo there, it's **iwlist wlan0 channel**.

Ok, you should check dmesg or syslog then and see if it displays an error message by the iwlwifi5k_cfg80211 that would give some clue as to whether it simply doesn't recognize the parameter (EU) or the whole option. Apparently at least Ralinks (a different chip manufacturer) version of cfg80211 only supports US or JP, so could be the same thing with Intel.

Another possibility would be to try setting the channel range through mac80211 with ```
options mac80211 ieee80211_regdom=64
```of course you'll probably have to change the module name to suit your modules, if your driver module doesn't make use of the generic mac80211, rather than a driver specific one (like with the cfg80211).

---

### Post by jdripper on 2009-09-18
OK, got it to see channel 13 finally, needed to have both lines in /etc/modprobe.d/options

```

options cfg80211 ieee80211_regdom=EU
options mac80211 ieee80211_regdom=64

```

---

### Post by t0mppa on 2009-09-19
Glad you finally got it working. Have to remember that the options clause doesn't change, even if the modules are named differently.

---

### Post by louigi600 on 2009-09-20
what do you get if you run this command :
iwlist wlan0 ch

Is the channel you are trying to use in the list ?
when you first try to issue the channel change is the interface up ... some cards do not work until you do:
ifconfig wlan0 up

what firmware are you using on the card ?
You should see something like this when the module is loaded :
[  133.634417] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-4965-2.ucode
[  133.663616] iwlagn 0000:03:00.0: loaded firmware version 228.57.2.21

---

### Post by jdripper on 2009-09-21
[@t0mppa]("http://swiss.ubuntuforums.org/member.php?u=787201")

Thanks !

[@louigi600]("http://swiss.ubuntuforums.org/member.php?u=910979")

Problem is now resolved. It had nothing to do with firmware, but the the region settings supported by the driver (kernel module).
Setting the right options as I indicated above allowed me to see the european reange and thus view and connect to my network.

---

