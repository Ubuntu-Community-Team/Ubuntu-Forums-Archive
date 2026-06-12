---
title: "Network intermittently dropping"
date: 2011-07-07
forum: Networking &amp; Wireless
---

### Post by hwttdz on 2011-07-07
My network seems to be dropping every few minutes to few hours.  There are a lot of networks in the area (apartment in NYC) and I wonder if it might be due to competing traffic.  Any ideas for how to tell what channels other networks are on? or other modifications to router settings that might improve performance in this situation?

Additionally the "Invalid Misc" in iwconfig is counting quite quickly.

---

### Post by jmoorse on 2011-07-12
Channel contention can cause this.  'iwlist [wlan adapter] scan' will show you nearby SSIDs

You can also use inssider to scan for networks near yours.  [http://www.metageek.net/products/inssider/linux/](http://www.metageek.net/products/inssider/linux/)

For B/G channels 1/6/11 are non-overlapping, you can try changing your channel to one of the 3 above.

---

### Post by garvinrick4 on 2011-07-12
channel 6 is router default in most all routers for 2.4 ghz so if you choose the 1 or 11 channel
as per post above you will have better chance on getting less traffic.
I like
```
nm-tool
```to check out others around me.
inSSider app worked real well in Windows as per linux have not had as much success will have
to try again though.

##What card and driver are you using:
```
 lspci -nnk | grep -iA2 network
```
Not iwlagn driver is it:

---

### Post by hwttdz on 2011-07-12
Here's the network situation, I'm superduper, I moved to 1 to avoid collisions with voila1, but if 6 and 11 are totally non overlapping, maybe I should go to 6 because then I would also avoid issues with A163 (but the power is so diminished at that point is it really an issue?).  

```
 BSSID              PWR  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID                                                                                      
 00:16:B6:67:5E:B3  -47       36        3    0   1  54e  WPA2 TKIP   PSK  superduperGx4                                                                              
 00:1F:33:D1:AD:38  -54       34        0    0  11  54e. WEP  WEP         Voila1                                                                                     
 30:46:9A:96:4B:50  -63       31        0    0  11  54e  WPA2 CCMP   PSK  GODLoVeSYoUmOrE                                                                            
 00:26:F3:1D:A1:65  -64       23        0    0   1  54 . WEP  WEP         A163                                                                                       
 00:1B:63:2A:F3:37  -66       48        0    0   6  54e. WPA2 CCMP   PSK  fir_brook                                                                                  
 A0:21:B7:B9:D8:A5  -67       49        0    0   3  54e. WPA2 CCMP   PSK  Moira67Cat                                                                                  
 00:23:97:FF:C5:33  -74       43        4    0   9  54   WPA2 TKIP   PSK  parallelexit                                                                                
 00:18:3A:C3:11:EA  -76       26        3    0   6  54   WEP  WEP         TAMUNA                                                                                      
 00:1E:4A:32:6A:E4  -80        3        0    0   6  54 . OPN              guest-net                                                                                   
 00:1E:4A:32:6A:E1  -81        2        0    0   6  54 . WPA  TKIP   MGT  paris                                                                                       
 00:1E:4A:32:6A:E5  -81        6        0    0   6  54 . WPA  TKIP   PSK  priv-psk                                                                                    
 00:14:6C:FD:E6:A8  -82       32        0    0  11  54 . WPA  TKIP   PSK  zacamina                                                                                    
 00:13:F7:BC:EF:00  -82        5        0    0   1  54 . WEP  WEP         EEFE                                                                                        
 00:22:6B:41:FC:0F  -82        6        0    0   1  54e  WPA  TKIP   PSK  Darci Network                                                                               
 00:1E:4A:32:6A:E0  -81        5        0    0   6  54 . WPA2 CCMP   MGT  athens                                                                                      
 00:1E:4A:32:6A:E2  -83        4        0    0   6  54 . OPN              rome                                                                                        
 1C:AF:F7:D0:4A:59  -83        5        0    0   6  54e. WEP  WEP         We Can Hear You Having Sex                                                                  
 00:24:6C:09:38:30  -83        4        0    0  11  54e. WPA2 CCMP   MGT  athens                                                                                      
 00:1E:4A:32:6A:E6  -81        7        0    0   6  54 . WEP  WEP         vocera-w       
```

My network adapter:

```
09:01.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
	Subsystem: Edimax Computer Co. Device [1432:7128]
	Kernel driver in use: rt61pci
```

---

### Post by jmoorse on 2011-07-12
Stick with 1 for a bit and let us know if you have the same issues.  Cheers,

---

