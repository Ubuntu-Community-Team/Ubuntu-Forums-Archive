---
title: "Netgear WG311v3 not working"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by gangasabu on 2009-03-30
Hi 
I have installed Netgear WG311v3 but was not successful in making it working. 
Details appeared on terminal is attached here with. Request some one to help me out in making the wireless network functioning.
Regards
Sabu

**_Following are the details_** 
sabu@sabu-desktop:~$ ndiswrapper -l
wg311v3 : driver installed
	device (11AB:1FAA) present
sabu@sabu-desktop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

sabu@sabu-desktop:~$ sudo modprobe ndiswrapper
sabu@sabu-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sabu@sabu-desktop:~$ sudo iwconfig wlan0 essid NETGEAR
sabu@sabu-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 7145
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:2a:b5:13:0e
Sending on   LPF/wlan0/00:1e:2a:b5:13:0e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
sabu@sabu-desktop:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
nameserver 192.168.1.1
sabu@sabu-desktop:~$ 

sabu@sabu-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          /usr/bin/poff: No pppd is running.  None stopped.
There is already a pid file /var/run/dhclient.eth0.pid with pid 7678
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1b:b9:6c:23:b5
Sending on   LPF/eth0/00:1b:b9:6c:23:b5
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
ppp0: ERROR while getting interface flags: No such device
Plugin rp-pppoe.so loaded.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1b:b9:6c:23:b5
Sending on   LPF/eth0/00:1b:b9:6c:23:b5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
sabu@sabu-desktop:~$ iwconfig wlan0 essid NETGEAR
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.
sabu@sabu-desktop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1e:2a:b5:13:0e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Memory:febe0000-febf0000 

sabu@sabu-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 7496
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:2a:b5:13:0e
Sending on   LPF/wlan0/00:1e:2a:b5:13:0e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
sabu@sabu-desktop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1e:2a:b5:13:0e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Memory:febe0000-febf0000 

sabu@sabu-desktop:~$ ping -c 3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 169.254.3.36 icmp_seq=1 Destination Host Unreachable
From 169.254.3.36 icmp_seq=2 Destination Host Unreachable
From 169.254.3.36 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2009ms
, pipe 3
sabu@sabu-desktop:~$

---

### Post by chili555 on 2009-03-30
May we please see:```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by gangasabu on 2009-04-01
Hi Chili555
Result of sudo iwlist wlan0 scan is given below. 
sabu@sabu-desktop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:50:F1:12:12:10
                    ESSID:"gangasabu"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

sabu@sabu-desktop:~$

---

### Post by chili555 on 2009-04-01
> wlan0 Scan completed :
Cell 01 - Address: 00:50:F1:12:12:10
ESSID:"gangasabu"However, you are trying to connect to 'NETGEAR':> sabu@sabu-desktop:~$ sudo iwconfig wlan0 essid NETGEARI also notice the router is protected with WPA. Where or how are you providing your encryption details?

---

