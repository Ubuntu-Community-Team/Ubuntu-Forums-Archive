---
title: "Wireless access point not associating"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by Jonnox on 2011-06-12
To start, I have done quite a bit of reading, including [_this archive post_]("http://ubuntuforums.org/archive/index.php/t-579084.html") but I am still unable to manually get my wireless to work. I need to get this working because I can't always have the luxury of the GUI based upon requirements so I need to be able to connect to a wireless router via script.

Quick background:

- Using Ubuntu 10.04
- Wireless works FINE if I use the GUI (no additional drivers required or anything)

```
root@root:/# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:F0:F6:CC:01
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"elliott_dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000276d072f63
                    Extra: Last beacon: 3180ms ago
                    IE: Unknown: 000D656C6C696F74745F646C696E6B
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: DD0600032F010001
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F0101001F0000
                    IE: Unknown: DD0C00037F020101270002A34000
                    IE: Unknown: DD1A00037F0301000000001CF0F6CC01021CF0F6CC0164002C011F08
```

Here is the result after the gui (I have x'd out the key):
```
root@root:/# iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"elliott_dlink"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:F0:F6:CC:01   
          Bit Rate=12 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:XXXX-XXXX-XX
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Now if I do it manually:

```
root@root:/# iwconfig wlan0 essid elliott_dlink mode Managed key XXXX-XXXX-XX

iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"elliott_dlink"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:XXXX-XXXX-XX
          Power Management:off
```

I have tried using ```
ap 00:1C:F0:F6:CC:01
``` as well in iwconfig with no real change. What am I doing wrong here? Because it is not associated I get the following when running dhclient on wlan0:

> Listening on LPF/wlan0/00:26:c6:42:69:fa
Sending on   LPF/wlan0/00:26:c6:42:69:fa
Sending on   Socket/fallback

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.

No working leases in persistent database - sleeping.

---

### Post by Jonnox on 2011-06-21
bump

---

