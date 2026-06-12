---
title: "Hornettek Janus Wireless USB adapter"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by OrangeMadness on 2010-10-12
I am trying to figure how to install this WLAN USB antenna and it is giving me some trouble, any help appreciated.

[http://www.hornettek.com/index.php/wi-fi-usb-dongle/janus](http://www.hornettek.com/index.php/wi-fi-usb-dongle/janus)

The chipset used is Realtek RTL8192su for which I loaded the driver using ndiswrapper.

```

louis@HP-4520s:/$ ndiswrapper -l
net8192su : driver installed
    device (0BDA:8174) present

```After installing the driver I can finally see the LEDs working and suprisingly I can scan for networks using this device:

```

louis@HP-4520s:/$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

wlan1     Scan completed :
          Cell 01 - Address: 00:1D:68:6C:E7:CB
                    ESSID:"CYTADCD7DF"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:24:17:7B:64:B5
                    ESSID:"CYTAE0B832"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:14:7F:1E:E8:97
                    ESSID:"SpeedTouch5AE5FF"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 02:E0:E7:EA:DE:08
                    ESSID:"ANY"
                    Protocol:IEEE 802.11g
                    Mode:Ad-Hoc
                    Frequency:2.457 GHz (Channel 10)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : none
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: 00:14:BF:BB:36:D9
                    ESSID:"Strovolos"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


```A good indication that the device is somehow working.


Now the problem is that in Network Manager the device always appears as Disabled. If i turn the laptop wireless ON I can see all available networks. When I turn laptop wireless off and plug the antenna I get the above iwlist scan but, in gnome GUI, the device appears disabled. 

It is worth mentioning the driver (net8192su) does not appear in lsmod

```

louis@HP-4520s:/$ lsmod | grep net
louis@HP-4520s:/$ 

```Any ideas? :confused:

---

