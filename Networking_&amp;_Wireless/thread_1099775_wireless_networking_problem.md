---
title: "wireless networking problem"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by urs4edal on 2009-03-18
I'm having problems with getting my Sony Vaio to connect to a wireless network.  Here are a few commands that I found on these forums, if you need more info let me know!

Sudo iwconfig
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Ad-Hoc  Frequency:2.457 GHz  Cell: Not-Associated   
          Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off 
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

pan0      no wireless extensions. 

sudo iwlist wlan0 scan

wlan0     Scan completed : 
          Cell 01 - Address: 56:EC:E9:8E:18:D1 
                    ESSID:"Ubuntu" 
                    Mode:Ad-Hoc 
                    Channel:10 
                    Frequency:2.457 GHz (Channel 10) 
                    Quality=79/100  Signal level:-55 dBm  Noise level=-127 dBm 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:tsf=00000005c57101f6 
                    Extra: Last beacon: 640ms ago 

sudo iwconfig wlan0

Please help if you can! I would really like to get this working.

---

### Post by inobe on 2009-03-18
i don't know about the commands' but what problems were you having just enabling the connection threw network manager ?

---

### Post by urs4edal on 2009-03-19
Well ubuntu recognizes my wireless card, and I can see wireless networks, when I try to connect it says acquiring a network address, and that's as far as it gets, it then comes up and says disconnected, and trys again until I cancel it.  The network I am trying to connect to has no wep or wpa encryption.

---

### Post by urs4edal on 2009-03-20
Anyone have any ideas on how I could fix this problem?

---

