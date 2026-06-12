---
title: "Not getting ip. Atheros. iwlist ok"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by cd-r80 on 2009-01-20
Hi! I have Acer Aspire laptop 5520. I have tried many ways to get wireless working On Hardy 64bit. AR5BXB63 !

Madwifi  No
Backports-modules  No
Ndiswrapper 1.53 + net5211  Sometimes
Compat-wireless  No

When ndiswrapper works or not I cannot find any differencces from dmesg. iwlist wlan0 scanning shows AP ok. Signal always good. it just does not get ip. I have tried two different APs. 

Has someone any answer why Im not getting IP? What was that unload reload ndiswrapper & modules what has helped someone?

---

### Post by steeleyuk on 2009-01-20
Open a terminal and try:

sudo dhclient wlan0

Edit: Is it connecting to the access point but not getting an IP?

---

### Post by cd-r80 on 2009-01-21
Sending on   LPF/wlan0/00:1d:.....
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.100 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.0.100 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
Trying recorded lease 192.168.0.100
No working leases in persistent database - sleeping.

wlan0     Scan completed :
          Cell 01 - Address: 00:........
                    ESSID:"Sitecom"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:98/100  Signal level:-33 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

---

