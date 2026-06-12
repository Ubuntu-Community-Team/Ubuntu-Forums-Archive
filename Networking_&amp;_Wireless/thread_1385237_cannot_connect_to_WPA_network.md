---
title: "cannot connect to WPA network"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by genjix on 2010-01-19
Hello,

I cannot connect to a WPA-PSK network that 2 friends on Windows computers can. Please help me since I only make a little money online and need the net to earn money for food, and I don't use Windows :(

Here's what I do:
```
airodump:
00:12:CF:6C:57:73  -66       99      286    7   2  54e. WPA  TKIP   PSK  suat1

root@l:/tmp# cat /etc/wpa_supplicant/net.conf 
network={                                     
ssid="suat1"                                  
key_mgmt=WPA-PSK                              
psk="a2341436z"                               
}                                             

root@l:/tmp# wpa_supplicant -Dwext -B -c /etc/wpa_supplicant/net.conf -i wlan0
root@l:/tmp# dhclient wlan0                                                   

Internet Systems Consortium DHCP Client V3.1.1                                
Copyright 2004-2008 Internet Systems Consortium.                              
All rights reserved.                                                          
For info, please visit http://www.isc.org/sw/dhcp/                            

mon0: unknown hardware address type 803
wmaster0: unknown hardware address type 801
mon0: unknown hardware address type 803
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1d:e0:a1:25:01
Sending on   LPF/wlan0/00:1d:e0:a1:25:01
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
Trying recorded lease 192.168.1.126
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

Trying recorded lease 192.168.2.135
PING 192.168.2.2 (192.168.2.2) 56(84) bytes of data.

--- 192.168.2.2 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
root@l:/tmp#

```

And the output of iwlist:
```
wlan0     Scan completed :
          Cell 01 - Address: 00:12:CF:6C:57:73
                    ESSID:"suat1"
                    Mode:Master
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=100/100  Signal level:-46 dBm  Noise level=-97 dBm
                    Encryption key:on
                    IE: Unknown: 00057375617431
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030102
                    IE: Unknown: 0706545249010D14
                    IE: Unknown: 200100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010020FF7F
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000003a1812181
                    Extra: Last beacon: 0ms ago

```

Not sure what's wrong here! Everything looks fine.

Thank you.

---

### Post by genjix on 2010-01-20
still couldn't get it to work :(

---

