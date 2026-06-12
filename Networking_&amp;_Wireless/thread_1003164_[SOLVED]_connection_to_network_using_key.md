---
title: "[SOLVED] connection to network using key?"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by rixtr66 on 2008-12-05
I just moved into a new apartment today and it includes wireless.
It requires a key wich i have and enter into the pass phrase box.
But when i hover the mouse over the network icon to see what its doing,
it says its waiting for the network key.Nothing pops up to enter it!
so how do i make this work?i have both keys but i dont know how to enter
the second key!could someone please help me!!!!!!
Peace
Rick

---

### Post by spiderbatdad on 2008-12-05
could you please provide more information?
What type of hidden connection is this WEP, WPA...?
What is your wireless interface? ```
iwconfig
```
What networks are available?```
sudo iwlist <interface ie, eth1> scan
```where <interface eth1> would be subsituted with an interface listed in iwlist...like wlan0, or eth1.

What version of Ubuntu are you running?

---

### Post by rixtr66 on 2008-12-05
The connection is WPA personal.
here is the output for iwconfig;

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"state street internet service"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:09:5B:47:DE:6C   
          Bit Rate=54 Mb/s   
          Power Management max timeout:0us  mode:All packets received
          Link Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
here is the output for the scan;

```
rick@rick-laptop:~$ sudo iwlist wlan0 scan
[sudo] password for rick: 
wlan0     Failed to read scan data : Resource temporarily unavailable

rick@rick-laptop:~$  sudo iwlist wlan0 scan
wlan0     Failed to read scan data :Resource temporarily unavailable


```
hmmm that didnt work:(
im using ubuntu 8.04,and using ndis wrapper for an atheros card.
i get open networks fine.this one requires a key wich i have.
i hope this is helpfull!!
Thanks!!
Rick

got it this time(the scan)The one im trying to connect to is HamWiFi.

```
rick@rick-laptop:~$  sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:9F:C0:3D
                    ESSID:"Chambers1"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:3/100  Signal level:-94 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:22:69:00:A0:E3
                    ESSID:"d8d9"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:02:6F:52:CA:67
                    ESSID:"HamWiFi"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:1E:E5:71:F0:04
                    ESSID:"Shermanation"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
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
          Cell 05 - Address: 00:13:46:1E:E8:AA
                    ESSID:"Scrooge's Internet!"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: 00:02:6F:52:CA:78
                    ESSID:"HamWiFi"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 00:12:0E:8A:58:76
                    ESSID:"07FX09042241"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 08 - Address: 00:1F:33:45:6B:6A
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-96 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 09 - Address: 00:1D:7E:18:7C:4E
                    ESSID:"OldGreg"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
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
          Cell 10 - Address: 00:12:0E:85:89:1A
                    ESSID:"07FX08018931"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/100  Signal level:-95 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 11 - Address: 00:80:C8:1E:06:31
                    ESSID:"default"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:6/100  Signal level:-92 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 12 - Address: 00:14:6C:F3:A0:1C
                    ESSID:"Black Cat"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
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
          Cell 13 - Address: 00:12:0E:42:12:26
                    ESSID:"06B408744704"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
          Cell 14 - Address: 00:13:10:0C:C6:F4
                    ESSID:"BillsPlace"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 15 - Address: 00:09:5B:47:DE:6C
                    ESSID:"state street internet service"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 16 - Address: 00:13:10:4D:38:3A
                    ESSID:"timber"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 17 - Address: 00:12:0E:1A:DA:A8
                    ESSID:"marjac"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0

rick@rick-laptop:~$ 


```
again hope this helps!!!

---

### Post by spiderbatdad on 2008-12-06
I have not used this wireless card, but I have seen a number of posts that say wpa is supported with the mad-wifi driver. Check out this simple guide...note in the comments about adding auth_pci to /etc/modules.
[http://brunoabinader.blogspot.com/2008/05/atheros-ar5bxb63-on-ubuntu-hardy-heron.html](http://brunoabinader.blogspot.com/2008/05/atheros-ar5bxb63-on-ubuntu-hardy-heron.html)
This guide discusses WPA2 [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
(unsuported by madwifi driver.)
WPA can be tricky...see also this thread:[http://ubuntuforums.org/showthread.php?t=798485](http://ubuntuforums.org/showthread.php?t=798485)

---

### Post by rixtr66 on 2008-12-06
i read through the links,theres nothing wrong with the drivers i have though.as i mentioned earlier,my wifi works fine,i just cant connect to 
one network,even though i have the key.i got it working briefly but i 
think it needs to be put in twice?
thanks!!
Rick

---

### Post by rixtr66 on 2008-12-06
Ok i tried wicd,and it connected briefly,the initial pass phrase works,
but i dont know how to add the network key?
](*,):-k
Rick

---

### Post by rixtr66 on 2008-12-06
Well i solved the puzzle!!i installed wicd,looked for the wireless access point in the list,selected it,selected wpa1/2,then chose,preshared key(this is what i missed)and viola!i got in!!!
thanks!!
peace
Rick\\:D/

---

