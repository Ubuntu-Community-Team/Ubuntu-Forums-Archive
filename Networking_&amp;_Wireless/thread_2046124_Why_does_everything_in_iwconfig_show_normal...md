---
title: "Why does everything in iwconfig show normal.."
date: 2012-08-22
forum: Networking &amp; Wireless
---

### Post by Moralz on 2012-08-22
[LEFT]But I have no internet access!! Im at my wits end! Please help...I tried connecting to a WEP network and used the CL. At first the ap wasnt associated and now it is (after i assigned it manually) now everything looks normal but i have no internet connection. WICD wont obtain an IP and I dont want to configure it every single time I want to connect to WEP, and dhclient -r wlan0 gives me a weird output (see below). Ive tried installing network manager, installing wifi-radar, reinstalled wicd and now im down from GUI methods to CL methods. Any help would be greatly appreciated. I can connect to WPA/WPA2 and open networks just fine.[/LEFT]
 [LEFT]
[/LEFT]
 [LEFT]This is the output of iwconfig after I connect manually. [/LEFT]
 [LEFT]
> 
[/LEFT]
 [LEFT]wlan0 IEEE 802.11bg ESSID:"2WIRE" 
Mode:Managed Frequency:2.462 GHz Access Point: b0:12:23:45:67:89
Bit Rate:12 Mb/s Tx-Power=16 dBm 
Retry min limit:7 RTS thr:off Fragment thr=off 
Encryption key: 1234-5678-12
Power Management: on
Link Quality=50/70 Signal level:-60 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:4 Invalid misc:2 Missed beacon:0[/LEFT]
 [LEFT]

This is the dhclient -t wlan0 output:[/LEFT]
 [LEFT]
> 
[/LEFT]
 [LEFT]Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/software/dhcp/](http://www.isc.org/software/dhcp/)[/LEFT]
 [LEFT]

[/LEFT]
   [LEFT]Listening on LPF/wlan0/00:0e:9b:cd:4e:18
Sending on LPF/wlan0/00:0e:9b:cd:4e:18
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping. 

Im using Ubuntu 10.04 (BT5R2), drivers are all up to date. Please help me, this is so annoying. Im tired of googling and seeing the same articles that are of no help. 
 
lspci -nnk
Kernel Module: ath9k[/LEFT]

---

### Post by Kirk Schnable on 2012-08-22
Are you sure DHCP is working on your wireless network?  Seriously, it looks like it isn't.  Make sure you don't have something (like an ACL or a MAC Address Filter) preventing your client from connecting and obtaining an IP.

It works as a static IP?  That leads me to believe something is blocking DHCP (either something on the AP or the firewall on the client).

Kirk

---

### Post by Moralz on 2012-08-23
As a static ip i have no internet connection, so no it doesnt work. DHCP is working because its assinging me ip's for WPA/WPA2 and open networks. This is so confusing. Its not just this WEP, its the other two like at school, and a family members house. The odds of my family member having mac filtering is crazy, especially considering with my regular windows pc i connect without issue. Thats why im pulling out my hair. I broke down and purchsed a wireless network card on the advice of a systems admin that tried connecting via teamviewer and had the same luck I had, none. Ill keep this updated. We connected to every type of network minus WEP, so it has to be an issue with backtrack and the card which is definitely not unheard of.

---

### Post by Kirk Schnable on 2012-08-23
> **Moralz said:**
> As a static ip i have no internet connection, so no it doesnt work. DHCP is working because its assinging me ip's for WPA/WPA2 and open networks. This is so confusing. Its not just this WEP, its the other two like at school, and a family members house. The odds of my family member having mac filtering is crazy, especially considering with my regular windows pc i connect without issue. Thats why im pulling out my hair. I broke down and purchsed a wireless network card on the advice of a systems admin that tried connecting via teamviewer and had the same luck I had, none. Ill keep this updated. We connected to every type of network minus WEP, so it has to be an issue with backtrack and the card which is definitely not unheard of.

We can see if your card has any known issues.

Could you post the output of:

```
lshw -C network
```

Kirk

---

