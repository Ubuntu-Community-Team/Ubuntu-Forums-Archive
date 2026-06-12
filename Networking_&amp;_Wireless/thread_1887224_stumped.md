---
title: "stumped"
date: 2011-11-26
forum: Networking &amp; Wireless
---

### Post by harpomason on 2011-11-26
connected and posting through linksys unsecured need to connect to coalkittylove did get connected few times but no internet just says connected and no connection info. I have been at this for days so tired of reading and trying everything. please help.


~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0



iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:6E:7E:07   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:20/100  Signal level:-83 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


sudo iwlist scan
[sudo] password for harpo: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:70:6E:7E:07
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:24:B2:13:CE:C0
                    ESSID:"coalkittylove"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
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
          Cell 03 - Address: 68:7F:74:3F:F0:C4
                    ESSID:"Cisco_WPS_9037"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
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
          Cell 04 - Address: 68:7F:74:3F:F0:C5
                    ESSID:"GoldBear-guest"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: E0:91:F5:0D:26:EB
                    ESSID:"rbh222"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 20:4E:7F:45:06:10
                    ESSID:"KQuad"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


$ sudo lshw -C network
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: e0:46:9a:07:ac:34
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netathuw driverversion=1.55+,09/30/2010,7.7.0.98 ip=192.168.1.100 link=yes multicast=yes wireless=IEEE 802.11g



$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid coalkittylove
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 8030322833653e7bb51741c6e6fa244ffa574c1bfd25ec42ab7aae6a753f2f0b
harpo@yoyo:~$ 
harpo@yoyo:~$ 
harpo@yoyo:~$ sudo ifdown -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
RTNETLINK answers: No such process
run-parts: executing /etc/network/if-down.d/postfix
run-parts: executing /etc/network/if-down.d/upstart
run-parts: executing /etc/network/if-down.d/wpasupplicant
dhclient3 -r -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 1966
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/e0:46:9a:07:ac:34
Sending on   LPF/wlan0/e0:46:9a:07:ac:34
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
ifconfig wlan0 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant


$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid coalkittylove
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 8030322833653e7bb51741c6e6fa244ffa574c1bfd25ec42ab7aae6a753f2f0b
harpo@yoyo:~$ 
harpo@yoyo:~$ 
harpo@yoyo:~$ sudo ifdown -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
RTNETLINK answers: No such process
run-parts: executing /etc/network/if-down.d/postfix
run-parts: executing /etc/network/if-down.d/upstart
run-parts: executing /etc/network/if-down.d/wpasupplicant
dhclient3 -r -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 1966
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/e0:46:9a:07:ac:34
Sending on   LPF/wlan0/e0:46:9a:07:ac:34
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
ifconfig wlan0 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant


$ sudo ifdown -v wlan0
ifdown: interface wlan0 not configured


$ sudo ifup -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver wext
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: waiting for "/var/run/wpa_supplicant.wlan0.pid":  0 (max. 5)
wpa_supplicant: creating sendsigs omission pidfile: /var/run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: wpa-ap-scan 1 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "coalkittylove" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: wpa-pairwise CCMP -- OK
wpa_supplicant: wpa-group CCMP -- OK
wpa_supplicant: wpa-key-mgmt WPA-PSK -- OK
wpa_supplicant: wpa-proto RSN -- OK
wpa_supplicant: enabling network block 0 -- OK

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/e0:46:9a:07:ac:34
Sending on   LPF/wlan0/e0:46:9a:07:ac:34
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
receive_packet failed on wlan0: Network is down
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPOFFER of 192.168.1.101 from 192.168.1.1
DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.101 from 192.168.1.1
bound to 192.168.1.101 -- renewal in 33659 seconds.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/ethtool
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/postfix
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant

---

