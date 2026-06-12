---
title: "USB adapter scans network but cannot connect"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by gshankar on 2009-05-10
Hi guys,
Sorry for the long post but I need help.

I set up an intel atom 330 mini-itx (motherboard 945GCLF2)box to serve as a media PC and has windows XP and Ubuntu 8.1 on it.

After going over the very useful threads on setting up the wireless network, I could get the my trendnet TEW424 wireless USB adapter to be recognized by the system.
Had to set up the ndiswrapper with the windows XP driver.

I then followed the instructions in the thread
 [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)
 and got to the point where I was able to connect to the internet JUST ONCE.
My  /etc/network/interfaces file looks like this
The router supports WPA with TKIP or AES. I have set it up for AES.
Anyways, I included both WPA/WPA2 settings in this file. SSID is not broadcast.
***************************************************************************
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid <MYSSID>
wpa-ap-scan 2
wpa-proto WPA RSN
wpa-pairwise TKIP CCMP
wpa-group TKIP CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <MYPSK GENERATED WITH WPA_PASSPHRASE>
***************************************************************************

Then I made changes to the  /etc/network/interfaces file and created the symbolic link in /etc/rcS.d/ S57wireless-network  to be able to connect to the wireless network upon bootup without having to restart the networking everytime.

After I rebooted following the changes, I have never been able to connect to the internet.

The messages that I see are as follows: It appears that the router to the connection cannot go through. I looked over and over again just to make  sure that my WPA pass phrase was correct. **Also, I can connect to the internet on this same system with the same adapter when using XP.**

*******************************************************************************
mediaPC:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                       There is already a pid file /var/run/dhclient.wlan0.pid with pid 10421
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/xx-xx-xx-xx-xx-xx  -- Adapter MAC addr
Sending on   LPF/wlan0/xx-xx-xx-xx-xx-xx-- Adapter MAC addr
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.11.1 port 67
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/ Adapter MAC addr
Sending on   LPF/wlan0/ Adapter MAC addr
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
***********************************************************************************

If I do  sudo iwlist scan,
I can see that the adapter is scanning for other networks that are broadcasting SSIDs and even listing them out. Mine does not show up on this list(could be because that I am not broadcasting my SSID?)
**************************************************************
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: XX:XX:XX:XX:XX:XX
                    ESSID:"XXXXXX"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key : on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s; 6 Mb/s; 5.5 Mb/s
                              2 Mb/s; 1 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: XX:XX:XX:XX:XX  
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:100/100  Signal level:-31 dBm  Noise level:-96 dBm
                    Encryption key : on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s; 6 Mb/s; 5.5 Mb/s
                              2 Mb/s; 1 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: XX:XX:XX:XX:XX:XX
                    ESSID:"xxxxxx"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key : on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s; 6 Mb/s; 5.5 Mb/s
                              2 Mb/s; 1 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

**************************************************************

Now, what could be the problem?:confused:


Do I need to set the "channel number" and anything that indicates that it is "managed mode"???

If so, could someone show what commands I need to use?



Thanks very much.

G. Shankar

---

### Post by gshankar on 2009-05-10
It appears that enabling the broadcast SSID seems to work. I do not understand why 
the command "wpa-ap-scan 2" is not picked up.
I modified the router settings to broadcast the SSID and then set "wpa-ap-scan 1".
This time it picked up.  
Wierd it worked that one time when I had set up the router to not broadcast.

Anyway, I would prefer it to work without broadcasting the SSID.

Any thoughts?


Thanks,
G. Shankar

---

