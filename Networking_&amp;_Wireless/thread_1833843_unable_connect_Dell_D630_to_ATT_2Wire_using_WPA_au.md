---
title: "unable connect Dell D630 to ATT 2Wire using WPA authentication"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by HornSpiel on 2011-08-26
Help.

I am unable to make a wireless connection to an ATT 2wire router ESSID called "WIGGERS" that I do not control. My Dell D630 does connect successfully to other WPA broadcasts. I am running Natty (11.04) with the default Unity interface.


iwconfig does see "WIGGERS",  but the Network Connections application on the menu bar eventually times out and asks for the authentication code. When I put in the code, it still does not connect. 

I do successfully connect to "WIGGERS" using another laptop running Win XP so I know the code is correct. The Windows machine indicates that it is using:
   Network authentication: WPA2-PSK
   Data encryption AES

Something that may be causing the problem is that the router is apparently putting out two signals (see iwlist output below). Both Cell 01 and Cell 02 have the same ESSID.

Below I have pasted output from lspci, iwconfig, and iwlist:

```
 Latitude-D630:~$ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
```

```

Latitude-D630:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensio22
Replicator
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ns.
wlan0  
   IEEE 802.11abg  ESSID:"WIGGERS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  lo ng limit:7   RTS thr:off   Fragment thr:off
          Power Management:off         
vboxnet0  no wireless extensions.

```

```
Latitude-D630:~$ iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:26:50:3F:AF:A9
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"WIGGERS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000025c47cd181
                    Extra: Last beacon: 1808ms ago
                    IE: Unknown: 000757494747455253
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010006
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 02 - Address: 12:C2:7D:15:FB:9A
                    Channel:1
                    Frequency:2.4102 GHz (Channel 1)
                    Quality=70/70  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:"WIGGERS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b88ed1719
                    Extra: Last beacon: 2144ms ago
                    IE: Unknown: 000757494747455253
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                        IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
.......................
```

---

### Post by praseodym on 2011-08-26
Hi,

just add one of the hardware adresses in the "BSSID" field in the NM applet:

```
Cell 01 - Address: [COLOR="Red"]00:26:50:3F:AF:A9[/COLOR]
```

better this one because of the link quality:

```
Cell 02 - Address: [COLOR="Red"]12:C2:7D:15:FB:9A[/COLOR]
                    Channel:1
                    Frequency:2.4102 GHz (Channel 1)
                    Quality=[COLOR="Red"]70/70[/COLOR]
```
Restart the connection:

```
sudo service network-manager restart
```

---

### Post by HornSpiel on 2011-08-26
It still does not connect. 
I put the BSSID here (Is this what I was supposed to do?):

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=200865&stc=1&d=1314396471[/IMG]

---

### Post by praseodym on 2011-08-26
IPv6 settings "ignored"? MAC-adress-filter in the router interface accepts new clients? Routerfirmware up-to-date?

---

### Post by HornSpiel on 2011-08-29
Yes IPv6 Settings are ignored.

I am connected to the router right now by wire (Ethernet).
Going to the router setup page [http://homeportal/](http://homeportal/) it says the system software is current.

I do not know how to check if the MAC-adress-filter in the router interface accepts new clients. If that is something in the router setup I do not see it. 
I do not have administrative access to the router so I cannot change settings or see advanced views of the router.

The owner is on vacation so I may need to wait for him to get back if it is a router issue.

Again thanks for your reply.

---

