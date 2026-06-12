---
title: "Wireless bouncing"
date: 2012-01-23
forum: Networking &amp; Wireless
---

### Post by clcbluemont on 2012-01-23
I am getting 30% packet loss, 0% packet loss and 100% packet at times to  the AP. And a lot of times dropping the connection all together. It seems  to have started right after latest kernel update on Kubuntu 11.10. Both  Network Manager and WICD react the same way, however with WICD it is  much easier to recover.


   
/sbin/iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"MiFi2372 5020"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 44:A7:CF:55:E1:BE   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr[IMG]http://static.linuxquestions.org/questions/images/smilies/redface.gif[/IMG]ff   Fragment thr[IMG]http://static.linuxquestions.org/questions/images/smilies/redface.gif[/IMG]ff
          Power Management[IMG]http://static.linuxquestions.org/questions/images/smilies/redface.gif[/IMG]ff
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:28  Invalid misc:31   Missed beacon:0






sudo iwlist wlan0 scan
[sudo] password for user: 
wlan0     Scan completed :
          Cell 01 - Address: 44:A7:CF:55:E1:BE
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key[IMG]http://static.linuxquestions.org/questions/images/smilies/redface.gif[/IMG]n
                    ESSID:"MiFi2372 5020"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003b7fef179
                    Extra: Last beacon: 460ms ago
                    IE: Unknown: 000D4D694669323337322035303230
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK







Our other MACOSX system is stable. dmesg is not saying anything. The following is the wicd.log file:

2012/01/22 20:40:29 :: Forced disconnect on
2012/01/22 20:40:29 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2012/01/22 20:40:29 :: /etc/network/if-down.d/avahi-autoipd returned 0
2012/01/22 20:40:29 :: Executing /etc/network/if-down.d/bind9 with params 
2012/01/22 20:40:29 :: /etc/network/if-down.d/bind9 returned 0
2012/01/22 20:40:29 :: Executing /etc/network/if-down.d/upstart with params 
2012/01/22 20:40:29 :: /etc/network/if-down.d/upstart returned 0
2012/01/22 20:40:29 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2012/01/22 20:40:29 :: /etc/network/if-down.d/wpasupplicant returned 0
2012/01/22 20:40:29 :: attempting to set hostname with dhclient
2012/01/22 20:40:29 :: using dhcpcd or another supported client may work better
2012/01/22 20:40:29 :: /sbin/dhclient -v -r wlan0
Internet Systems Consortium DHCP Client 4.1.1-P1
Copyright 2004-2010 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/f4:ec:38:8b:a3:17
Sending on   LPF/wlan0/f4:ec:38:8b:a3:17
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
2012/01/22 20:40:29 :: /sbin/ip route flush dev wlan0
2012/01/22 20:40:29 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2012/01/22 20:40:29 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2012/01/22 20:40:29 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2012/01/22 20:40:29 :: /etc/network/if-post-down.d/wireless-tools returned 0
2012/01/22 20:40:29 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2012/01/22 20:40:29 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2012/01/22 20:40:29 :: wpa_cli -i wlan0 terminate
2012/01/22 20:40:29 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2012/01/22 20:40:29 :: /etc/network/if-down.d/avahi-autoipd returned 0
2012/01/22 20:40:29 :: Executing /etc/network/if-down.d/bind9 with params 
2012/01/22 20:40:29 :: /etc/network/if-down.d/bind9 returned 0
2012/01/22 20:40:29 :: Executing /etc/network/if-down.d/upstart with params 
2012/01/22 20:40:29 :: /etc/network/if-down.d/upstart returned 0
2012/01/22 20:40:29 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2012/01/22 20:40:29 :: /etc/network/if-down.d/wpasupplicant returned 0
2012/01/22 20:40:29 :: attempting to set hostname with dhclient
2012/01/22 20:40:29 :: using dhcpcd or another supported client may work better
2012/01/22 20:40:29 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.1.1-P1
Copyright 2004-2010 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/38:60:77:0d:c7:76
Sending on   LPF/eth0/38:60:77:0d:c7:76
Sending on   Socket/fallback
2012/01/22 20:40:29 :: /sbin/ip route flush dev eth0
2012/01/22 20:40:30 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2012/01/22 20:40:30 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2012/01/22 20:40:30 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2012/01/22 20:40:30 :: /etc/network/if-post-down.d/wireless-tools returned 0
2012/01/22 20:40:30 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2012/01/22 20:40:30 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2012/01/22 20:42:39 :: found backend in configuration external
2012/01/22 20:43:33 :: setting use global dns to 0
2012/01/22 20:43:33 :: setting global dns
2012/01/22 20:43:33 :: global dns servers are   
2012/01/22 20:43:33 :: domain is 
2012/01/22 20:43:33 :: search domain is 
2012/01/22 20:43:33 :: setting wireless interface wlan0
2012/01/22 20:43:33 :: setting wired interface eth0
2012/01/22 20:43:33 :: setting wpa driver wext
2012/01/22 20:43:33 :: setting automatically reconnect when connection drops 0
2012/01/22 20:43:33 :: setting backend to external
2012/01/22 20:43:33 :: Setting dhcp client to 0
 







The following says Disabled because the connection dropped twice while I was composing this.

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: 38:60:77:0d:c7:76
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e  driverversion=1.3.10-k2 firmware=0.13-4 latency=0 link=no multicast=yes  port=twisted pair
       resources: irq:48 memory:fe600000-fe61ffff memory:fe624000-fe624fff ioport:f080(size=32)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1.4
       logical name: wlan0 
       serial: f4:ec:38:8b:a3:17
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc  driverversion=3.0.0-15-generic firmware=1.3 link=no multicast=yes  wireless=IEEE 802.11bgn


Any logging that I can do to figure out why the connection is bouncing,  dropping, intermittent? Thank you for any direction that can be  provided. Could this have been that plasma ball from the Sun that blew past Sunday?

---

