---
title: "Cant obtain ip adress (DWA-140)"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by simon82 on 2009-10-31
i can find my router (dlink) but i cant obtain an ipadress. Ive tried to remove Networkmanager and install WICD 1.61 instead no luck. Ive also tried to remove my wpa2 and run without encryption with no sucess. Any ideas ?

Following the howto post guide here:

**_lsusb:_** Bus 001 Device 002: ID 07d1:3c09 D-Link System DWA-140 802.11n Adapter [ralink rt2870]

**_iwconfig:_** 
wlan0     IEEE 802.11bgn  ESSID:"dlink"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=3 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**_lsmod | grep "rt2*"_**:
server@server-desktop:~$ lsmod | grep "rt2*"
rt2870sta             488820  0 
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181236  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
crc_ccitt               1852  1 rt2800usb

**_dmesg:_**
[   17.744811] rt2800usb 1-1:1.0: firmware: requesting rt2870.bin
[   18.181047] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.523674] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   26.994940] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.251860] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   75.671247] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   75.892720] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   75.941292] wlan0: authenticate with AP xx:XX:XX:XX:XX:XX
[   75.946539] wlan0: authenticate with AP xx:XX:XX:XX:XX:XX
[   75.952067] wlan0: authenticated
[   75.952075] wlan0: associate with AP xx:XX:XX:XX:XX:XX
[   75.955588] wlan0: RX AssocResp from xx:XX:XX:XX:XX:XX (capab=0x421 status=0 aid=3)
[   75.955595] wlan0: associated
[   75.964199] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   86.540019] wlan0: no IPv6 routers present
[  109.923227] wlan0: deauthenticating by local choice (reason=3)
[  110.132713] ADDRCONF(NETDEV_UP): wlan0: link is not ready

**_sudo lshw -C network:_**
*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1b:11:1d:d0:b8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

**_iwlist scan:_**
wlan0     Scan completed :
          Cell 01 - Address: XX:XX:XX:XX:XX
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=43 dBm  
                    Encryption key:off
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003419b2180
                    Extra: Last beacon: 1296ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD1E00904C334E101DFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050500000000000000000000000000000000000000
                    IE: Unknown: 2D1A6E101DFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D18010500000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F202010100000364000027A4000041435E0061322F00

**_lsb_release -d_** Ubuntu 9.10
** _ uname -mr_ ** 2.6.31-14-generic i686

**_sudo /etc/init.d/networking restart_**
 * Reconfiguring network interfaces...                         [ OK ]

---

### Post by simon82 on 2009-10-31
sorry for BUMP but i realy could use some help.

---

