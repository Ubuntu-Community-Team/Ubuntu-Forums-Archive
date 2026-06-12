---
title: "T61 Ubuntu 9.04 , can not do WEP!HELP ME!!"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by starimpact on 2009-08-31
[B]First, i am sure the wep password is right.My wireless card's driver is right, because the Ubuntu supports it.And, the card can find the wireless router also.I have tried all kind of wep format, but none can the router accept.I search the answer in the web, somebody has the same problem in the Ubuntu 9.04, but their solutions are not fit mine.
The following is my card information.
Please Help me! Why can not I connect to my secured mireless router?

I tried the tool wcid also, but it could not fix it also.

My wirelesscard is: Intel Wireless WiFi Link 4965AG.
OS: Ubuntu 9.04 64Bit.[/B]
---------------------------------------------------------------

star@star-si:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"MERCURY"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


star@star-si:~$ sudo iwlist wlan0 scan 
wlan0     Scan completed :
          Cell 01 - Address: 00: xx: xx: xx: xx: xx
                    ESSID:"MERCURY"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=74/100  Signal level:-60 dBm  Noise level=-127 dBm
                    Encryption key: on
                    IE: Unknown: 00074D455243555259
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 0706434E20010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000015ed73c181
                    Extra: Last beacon: 84ms ago

star@star-si:~$ sudo iwlist wlan0 scan 
wlan0     Scan completed :
          Cell 01 - Address: 00: xx: xx: xx: xx: xx
                    ESSID:"MERCURY"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=74/100  Signal level:-60 dBm  Noise level=-127 dBm
                    Encryption key: on
                    IE: Unknown: 00074D455243555259
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 0706434E20010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000015ed73c181
                    Extra: Last beacon: 84ms ago

star@star-si:~$ sudo iconfig wlan0 essid ... key ...

star@star-si:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00: xx: xx: xx: xx: xx
Sending on   LPF/wlan0/00: xx: xx: xx: xx: xx
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---------------------------------------------------------------

---

### Post by starimpact on 2009-08-31
why no body help me?my wireless card works well with Ubuntu 8.04.I think the 9.04 has some bug.I hope 9.10 will fix this problem.

---

### Post by dbalascak on 2009-08-31
I havenot been able to get wicd to work automatically yet either.  I did get WEP working though.  First of all can you use a static IP address?  This just takes one thing out of the equation. You can look at routing tables if it isn't waiting for a DHCP adresss. If you can't no big deal. 
Either way, when your wireless card is connecting, execute the following in another window. *sudo iwconfig wlan0 key XXXXXXXXXXXX*  The key should be in the format 1234567890abcdef if you are using the 40/128 bit key.  Lower case. If that connects, then the issue is with  the WEP key interface configuration.

---

### Post by webdevelopment on 2009-09-16
> **dbalascak said:**
> I havenot been able to get wicd to work automatically yet either.  I did get WEP working though.  First of all can you use a static IP address?  This just takes one thing out of the equation. You can look at routing tables if it isn't waiting for a DHCP adresss. If you can't no big deal. 
Either way, when your wireless card is connecting, execute the following in another window. *sudo iwconfig wlan0 key XXXXXXXXXXXX*  The key should be in the format 1234567890abcdef if you are using the 40/128 bit key.  Lower case. If that connects, then the issue is with  the WEP key interface configuration.

can you translate this to english for new ubuntu users?

---

