---
title: "WPA works in windows, not ubuntu"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by gatorbrit on 2009-10-14
My wireless works for many different networks in ubuntu - home, coffee shop etc.  But for one WPA network it refuses to connect - while windows does just fine on it (same laptop - dual boot).

The network manager shows that the wireless network is found and it seems to be trying to connect.  It asks me for the password and then nothing happens. 

Thanks

The card is an intel 3945ABG pro/wireless

Some output...

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"radiobldg18"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```


```
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:6E:AC:37:80
                    ESSID:"radiobldg18"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/100  Signal level:-79 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: Unknown: 000B726164696F626C64673138
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010004FF7F
                    IE: Unknown: DD0C00037F020101000002A44000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000122a7ea9037
                    Extra: Last beacon: 1108ms ago
          Cell 02 - Address: 00:18:6E:AC:37:82
                    ESSID:"secondary"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/100  Signal level:-78 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: Unknown: 00097365636F6E64617279
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010004FF7F
                    IE: Unknown: DD0C00037F020101000002A44000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000122a7ea9526
                    Extra: Last beacon: 1108ms ago
          Cell 03 - Address: 00:18:6E:AC:FA:00
                    ESSID:"radiobldg18"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/100  Signal level:-76 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: Unknown: 000B726164696F626C64673138
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010004FF7F
                    IE: Unknown: DD0C00037F020101000002A44000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000007fc013c54f
                    Extra: Last beacon: 1296ms ago

pan0      Interface doesn't support scanning.
```


```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)


```

---

### Post by bkratz on 2009-10-14
[quote=gatorbrit;8105830]My wireless works for many different networks in ubuntu - home, coffee shop etc.  But for one WPA network it refuses to connect - while windows does just fine on it (same laptop - dual boot).

The network manager shows that the wireless network is found and it seems to be trying to connect.  It asks me for the password and then nothing happens. 

Thanks

wlan0     Scan completed :
          Cell 01 - Address: 00:18:6E:AC:37:80
                    ESSID:"radiobldg18"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/100  Signal level:-79 dBm  Noise level=-127 dBm
                    Encryption key:on
  
          Cell 02 - Address: 00:18:6E:AC:37:82
                    ESSID:"secondary"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/100  Signal level:-78 dBm  Noise level=-127 dBm
                    Encryption key:on
  
          Cell 03 - Address: 00:18:6E:AC:FA:00
                    ESSID:"radiobldg18"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/100  Signal level:-76 dBm  Noise level=-127 dBm
                    Encryption key:on

quote]

Which network are you trying to connect to?  Two of the three shown have just about the same signal strength and the same frequency. The other has a different frequency (channel).  I could see the system getting confused it you are trying to connect with either of the first two.

---

### Post by gatorbrit on 2009-10-14
Good question - trying to connect to 1 or 3 "radiobldg18"   
is there a way I can force it to pick?

In the box in the top right of the screen it indicates both "radiobldg" and "secondary"   I checked the little circle next to "radiobldg" and it asked me for the password, but didn't connect.

---

### Post by bkratz on 2009-10-14
> **gatorbrit said:**
> Good question - trying to connect to 1 or 3 "radiobldg18"   
is there a way I can force it to pick?

In the box in the top right of the screen it indicates both "radiobldg" and "secondary"   I checked the little circle next to "radiobldg" and it asked me for the password, but didn't connect.



Yes, but I guess what I was saying was how do you know which radiobldg18 is the one you are trying to connect to?  If it was number one, I could see it interfering with selection number two(secondary).

---

### Post by gatorbrit on 2009-10-14
> **bkratz said:**
> Yes, but I guess what I was saying was how do you know which radiobldg18 is the one you are trying to connect to?  If it was number one, I could see it interfering with selection number two(secondary).

I see your point- so how can I force it to pick the one i want.

---

