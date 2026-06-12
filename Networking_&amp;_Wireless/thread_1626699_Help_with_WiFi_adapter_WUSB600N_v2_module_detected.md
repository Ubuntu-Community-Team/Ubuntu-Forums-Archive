---
title: "Help with WiFi adapter WUSB600N v2: module detected but no connection - DHCP error"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by Walmit on 2010-11-20
[COLOR=#000000][FONT=Arial]Hello all,[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I  have just started to work on Ubuntu (Ubuntu 10.4 LTS) and I am having  some problems to get a WUSB600N vers. 2 802.11n adapter working.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I have followed the procedure described at [/FONT][/COLOR][[COLOR=#000099][FONT=Arial]_http://homecommunity.cisco.com/t5/Wireless-Adapters/UBUNTU-WUSB600N-v2-WORKS/m-p/318026_[/FONT][/COLOR]]("http://homecommunity.cisco.com/t5/Wireless-Adapters/UBUNTU-WUSB600N-v2-WORKS/m-p/318026")[COLOR=#000000][FONT=Arial] and [/FONT][/COLOR][[COLOR=#000099][FONT=Arial]_http://ubuntuforums.org/showthread.php?t=1580657&highlight=WUSB600N_[/FONT][/COLOR]]("http://ubuntuforums.org/showthread.php?t=1580657&highlight=WUSB600N")[COLOR=#000000][FONT=Arial] . The compilation has been successful and I can see the kernel loaded an the module detected:[/FONT][/COLOR][INDENT] ```
adrien@ubuntu:/$ lsmod | grep rt3572
rt3572sta             612272  1

adrien@ubuntu:/$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c510 Logitech, Inc. Cordless Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 1737:0079 Linksys
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``` [/INDENT][COLOR=#000000][FONT=Arial]The wireless adapter is detected by the system and it can scan the neighboring APs (cf. below with MAC address made unreadable):[/FONT][/COLOR][INDENT]```
adrien@ubuntu:/$ sudo iwlist ra0 scan
[sudo] password for adrien:
ra0       Scan completed :
          Cell 01 - Address: --:--:--:--:--:--:-- 
                    Protocol:802.11g
                    ESSID:"Coucou1"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:83/100  Signal level:-57 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s
          Cell 02 - Address: --:--:--:--:--:--:-- 
                    Protocol:802.11b/g/n
                    ESSID:"Coucou2"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-93 dBm  Noise level:-88 dBm
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    IE: Unknown: DD0E0050F204104A0001101044000101

adrien@ubuntu:/$ iwconfig ra0
ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT3572STA"
          Mode:Auto  Frequency=2.462 GHz  Access Point: --:--:--:--:--:--:--   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-55 dBm  Noise level:-55 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``` [/INDENT][COLOR=#000000][FONT=Arial]However, I don’t get any IPV4 address for this WiFi adapter (but apparently, the adapter can well received packets):[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]adrien@ubuntu:/$ ifconfig ra0[/FONT][/COLOR][INDENT]```
ra0       Link encap:Ethernet  HWaddr 00:25:9c:b4:20:bf  
          adr inet6: fe80::225:9cff:feb4:20bf/64 Scope:Lien
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:8067 erreurs:0 :0 overruns:0 frame:0
          TX packets:19060 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:977780 (977.7 KB) Octets transmis:1327176 (1.3 MB)
``` [/INDENT][COLOR=#000000][FONT=Arial]Applying the command “sudo iwconfig ra0 essid Coucou1” did not improve the situation and did not return any error message.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Applying  the command “sudo dhclient ra0” did not provide a IP address (there is  however a DHCP server on my router that is correctly working with my  Windows PC and I have deactivated the WPA key on my WiFi for this  test):[/FONT][/COLOR][INDENT]```
sudo dhclient ra0
There is already a pid file /var/run/dhclient.pid with pid 5960
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/ra0/00:25:9c:b4:20:bf
Sending on   LPF/ra0/00:25:9c:b4:20:bf
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
``` [/INDENT][COLOR=#000000][FONT=Arial]Since  my knowledge about Linux is quite limited, I suspect I am missing  something very obvious. I had a brief look on the forum but I did not  find any similar issue (there are several posts about WUSB600N but I did  not find an answer to this problem).[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Thanks in advance for any help[/FONT][/COLOR]

---

### Post by Walmit on 2010-11-21
Any ideas or suggestion about this problem? There are similar posts ([http://ubuntuforums.org/showthread.php?t=1346760&highlight=WUSB600N+DHCP](http://ubuntuforums.org/showthread.php?t=1346760&highlight=WUSB600N+DHCP)) on this forum but no solution is proposed. 
Any help will be very appreciated. 
Thanks a lot.

---

### Post by Walmit on 2010-11-21
YESSSS, after a lot of tries (and chocolate bars), it finally works.
For information, I restart all the procedure from zero, following the explanation given at [http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb600n-driver-and-dlink-dwl-ag132-driver-622449/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb600n-driver-and-dlink-dwl-ag132-driver-622449/). Previously, I had not blacklisted the default generic drivers and I had to add the following 
```
blacklist rt2860sta
blacklist rt2870sta
blacklist rt3090sta

blacklist rt2x00usb
blacklist rt2500usb
blacklist rt2800usb
blacklist rt73usb
```in /etc/modprobe.d/blacklist.conf.

I also added
```
auto ra0
iface ra0 inet dhcp
allow-hotplug ra0
```in /etc/network/interfaces

---

