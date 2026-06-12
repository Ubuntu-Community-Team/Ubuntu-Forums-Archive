---
title: "No Internect Connection after extensive troubleshooting"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by linuxquestusa on 2009-01-14
Trouble shot the following:


**Version**: Upgraded from _Gutsy Gibbon_ to Hardy Heron LTS 8.04

**Windows Wireless Drivers**: rt2500usb, Hardware present: YES  (This info was obtained by going to SYSTEM--WINDOWS WIRELESS DRIVERS)

**Physical connection**: Plugged the _Linksys WUSB54G v4 wireless adapter_ into a USB port that is in the back of the computer.

**Network Manager**: Enabled Roaming on wireless and wired networks.  Switched from enabling roaming on wireless and then disabling roaming on wireless to enabling roaming on wired networks to disabling roaming on wired network while having roaming disabled on wireless network.


**Interface**: Typed the following command:  [U]sudo gedit /etc/network/interfaces
[/U]
_and received the following_:   

# This file describes the network interfaces available on your system 
# and how to activate them. For more information, see interfaces(5). 

# The loopback network interface 
auto lo 
iface lo inet loopback 

# The primary network interface 

iface wlan0 inet dhcp 
wpa-psk (uses a 64 number password key) 
wpa-driver wext 
wpa-key-mgmt WPA-PSK 
wpa-proto WPA 
wpa-ssid 05B418169191

auto wlan0 

iface eth0 inet dhcp 

auto eth0


**Note**: After “iface wlan0 inet dhcp ” typed in following:

ip address: 192.168.1.15
gateway: 192.168.1.15
dns-nameservers: 192.168.1.15
netmask: 255.255.255.0

Saved these settings and then open Firefox and still couldn't connect to the Internet.


**Router**: Shut computer down along with the router.  Waited 10 seconds then turned router back on.

Started computer and opened a Terminal Session and typed the following:

**sudo /etc/init.d/networking restart**

opened Firefox to connect to the Internet and still no connection.

After making these modifications, shut down computer and waited 30 seconds and then turned computer back on.  Still no Internet connection.


Typed the following command: **iwconfig**

_and received the following_:

lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:"05B418169191"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:12:0E:16:AD:E6   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=48/100  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 


_Typed the following command_: **iwlist scan**

_and received the following_:

lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wmaster0  Interface doesn't support scanning. 

wlan0     Scan completed : 
          Cell 01 - Address: 00:12:0E:16:AD:E6 
                    ESSID:"05B418169191" 
                    Mode:Master 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=49/100  Signal level=-65 dBm  
                    Encryption key:on 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s 
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                              36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Extra:tsf=000000099b620c80 


_Typed the following command_:  **route**

_and received the following_:

Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
localnet        *               255.255.255.0   U     0      0        0 eth0 
localnet        *               255.255.255.0   U     0      0        0 wlan0 
169.254.0.0     *               255.255.0.0     U     1000   0        0 wlan0 
default         Michael         0.0.0.0         UG    100    0        0 wlan0 
default         Michael         0.0.0.0         UG    100    0        0 eth0 



**Comments**: What more can I do to get this to work?****

---

### Post by zika on 2009-01-14
I think I can see some problems (disclaimer:I'm not experienced in wireless):
```
iface wlan0 inet **dhcp**
```is in contradiction with (see below for correct syntax):
```
ip address: 192.168.1.15
gateway: 192.168.1.15
dns-nameservers: 192.168.1.15
netmask: 255.255.255.0
```1. use **static** instead of [B]dhcp
[/B]2. list from **/etc/network/interfaces** should look:```
address 192.168.1.15
gateway 192.168.1.15
netmask 255.255.255.0
```3. ```
 nameserver 192.168.1.15
``` should go to **/etc.resolv.conf**.

---

